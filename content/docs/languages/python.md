---
title: "Python"
---

# File renaming
Used this script to parse a csv and rename a bunch of terrible files
```Python
import csv
from enum import IntEnum
import os

class Headers(IntEnum):
    ID = 0
    NAME = 1
    PARENT_ID = 2

attachmentsDir = './FLDOE_Attachments/Attachments/'
nameById = {}

with open('fdoe_att_list.csv') as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=',')
    for row in csv_reader:
        fullName = "(parentId_%s)_(id_%s)_%s" % (row[Headers.PARENT_ID], row[Headers.ID], row[Headers.NAME])
        nameById[row[Headers.ID]] = fullName

for file in os.listdir(attachmentsDir):
    if file in nameById:
        newName = nameById[file]
        newName = newName.replace('/', '-')
        newName = newName.replace(' ', '_')
        newName = newName.replace(':', '-')
        
        os.rename(attachmentsDir + file, attachmentsDir + newName)
```
