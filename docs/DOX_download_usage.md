# Download and Usage Instructions

Replace placeholder S3 values after the dataset is
uploaded.

## Dataset Root

Current internal dataset root:

```text
root
```

The public release should preserve the current experiment-batch structure:

```text
Doxorubicin_Induced_Heart_Failure_Dataset/
└── dox/
    ├── <date-or-date-time-batch>/
    │   ├── C- or Con-labeled files
    │   ├── model-group files
    │   └── administered-treatment-group files
    ├── condition_optimization/
    ├── Tanshinone/                 # included imaging files only
    └── Ganoderma/
```


## AWS S3 Access

After upload to AWS S3, users should be able to browse or download the dataset
from a public bucket.

S3 URI:

```text
s3://<bucket-name>/<optional-prefix>/
```

Example command:

```bash
aws s3 sync --no-sign-request \
  s3://<bucket-name>/<optional-prefix>/ \
  ./Doxorubicin_Induced_Heart_Failure_Dataset/
```
