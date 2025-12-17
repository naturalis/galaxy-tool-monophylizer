# Development and Release Documentation

## Releasing to ToolShed

How to submit a tool to the Galaxy ToolShed:

1. Create an account on the [ToolShed](https://toolshed.g2.bx.psu.edu/)
2. Create a $HOME/.planemo.yml file with the following content:

```yaml
shed_username: $USER # your ToolShed username
sheds:
  toolshed:
    key: $KEY        # your ToolShed API key, under 'User > API Keys'
    email: $EMAIL    # your ToolShed email
    password: $PASS  # your ToolShed password
```

3. Install Planemo:

```bash
pip install planemo
```

4. Validate your tool XML:

```bash
planemo lint monophylizer.xml
```

5. Test your tool:

```bash
planemo test monophylizer.xml
```

6. Publish your tool:

```bash
planemo shed_create --shed_target toolshed
```

7. Update your tool:

```bash
planemo shed_update --shed_target toolshed
```

## CI/CD and Testing

This repository includes GitHub Actions workflows for continuous testing and publishing:

### Automated Publishing to Galaxy Toolshed

The `planemo-publish.yml` workflow automatically publishes the tool to the Galaxy Toolshed when a new version is tagged. To use this workflow:

1. Set up the following repository secrets (Settings > Secrets and variables > Actions):
   - `USER`: Your Galaxy Toolshed username
   - `KEY`: Your Toolshed API key (found under User > API Keys)
   - `EMAIL`: Your Toolshed account email
   - `PASS`: Your Toolshed account password

2. Create a new tag to trigger publishing:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```

The workflow will automatically:
- Install Planemo and dependencies
- Create the Planemo configuration file
- Update the existing tool in the toolshed (or create it if it doesn't exist yet)

### Viewing Test Outputs

The `planemo-test.yml` workflow automatically runs tests on every push and pull request. It captures all temporary output files generated during testing and uploads them as artifacts. You can:

1. Go to the Actions tab in GitHub
2. Click on a workflow run
3. Scroll down to "Artifacts" section
4. Download `planemo-test-outputs` to view the actual output files generated during testing
5. The workflow logs also display the contents of TSV output files inline

This is useful for:
- Debugging test failures
- Verifying the actual output format
- Updating test-data files when the tool behavior changes
