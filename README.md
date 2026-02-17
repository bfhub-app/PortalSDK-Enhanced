# PortalSDK Community - bfhub.app

## Differences

TBD

## Development

### Cloning the Repository

Clone normally - the SDK files are already included via git subtree:

```bash
git clone git@github.com:bfhub-app/PortalSDK-Enhanced.git
```

The `sdk` folder contains two subtrees:
- `sdk/sdk-community` - PortalSDK Community files
- `sdk/sdk-mirror` - PortalSDK Mirror files

### Updating SDK Files from Upstream

To pull latest changes from the upstream repositories:

```bash
# Update sdk-community
git subtree pull --prefix=sdk/sdk-community git@github.com:bfhub-app/PortalSDK-Community-Mirror.git main --squash

# Update sdk-mirror
git subtree pull --prefix=sdk/sdk-mirror git@github.com:bfhub-app/PortalSDK-Mirror.git main --squash
```

### Triggering the Update Workflow From Other Repos

This workflow supports both `repository_dispatch` and `workflow_call`.

Repository dispatch (event type: `sdk_check_update`):

```bash
curl -X POST \
	-H "Accept: application/vnd.github+json" \
	-H "Authorization: Bearer <TOKEN>" \
	https://api.github.com/repos/bfhub-app/PortalSDK-Enhanced/dispatches \
	-d '{"event_type":"sdk_check_update"}'
```

Workflow call (from another repo):

```yaml
jobs:
	trigger-sdk-update:
		uses: bfhub-app/PortalSDK-Enhanced/.github/workflows/sdk_check-update.yml@main
		with:
			reason: "sync from upstream"
```

> Created by Nano
