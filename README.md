---
services: data-lake-analytics
platforms: dotnet
author: saveenr
---

# USQL/Cognitive Imaging OCR Hello World


```
REFERENCE ASSEMBLY ImageCommon;
REFERENCE ASSEMBLY FaceSdk;
REFERENCE ASSEMBLY ImageEmotion;
REFERENCE ASSEMBLY ImageTagging;
REFERENCE ASSEMBLY ImageOcr;


@ocrs =
    PROCESS @imgs
    PRODUCE FileName,
            Text string
    READONLY FileName
    USING new Cognition.Vision.OcrExtractor();
```

