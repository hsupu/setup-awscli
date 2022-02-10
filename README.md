# setup-awscli

A GitHub Action to set up aws-cli v2 **in linux job**.

The action follows instructions in https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

You can directly copy the steps from `action.yml` to your job.

Usage:

```yaml
- name: setup awscli
  uses: hsupu@setup-awscli@v1
  with:
    # these are default values
    install-dir: /usr/local/aws-cli
    bin-dir: /usr/local/bin

- name: s3 put-object
  # https://docs.aws.amazon.com/cli/latest/reference/s3api/put-object.html#examples
  run: |
    echo Hello World > a.txt
    aws s3api put-object --bucket <bucket> --key <key> --body a.txt
  env:
    # https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html
    AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
    AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    AWS_DEFAULT_REGION: 'us-east-1'
```

Notice: add action secrets: `AWS_ACCESS_KEY_ID` `AWS_SECRET_ACCESS_KEY`.

You can also find AWS official-released GitHub Actions in https://github.com/aws-actions .
