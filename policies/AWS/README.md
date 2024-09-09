# Copyright (c) 2023 EPAM Systems, Inc.
#
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

policies:
  - name: s3-set-bucket-encryption
    comment: '020016182700'
    description: |
      Ensure S3 bucket encryption is enabled with AES256 encryption algorithm
    resource: aws.s3
    filters:
      - type: value
        key: "BucketName"
        value: "my-secure-bucket"
      - type: value
        key: "Encryption"
        value: "None"
    actions:
      - type: set-bucket-encryption
        crypto: AES256
        enabled: True
