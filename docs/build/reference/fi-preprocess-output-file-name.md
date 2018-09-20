---
title: -Fi （前置處理輸出檔名稱） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f69a4ab16956924e3bcfd785c6a86c7ac238b36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431550"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (前置處理輸出檔名稱)

指定輸出檔名稱[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)編譯器選項會將前置處理過的輸出。

## <a name="syntax"></a>語法

```
/Fipathname
```

#### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|`pathname`|所產生的輸出檔案的路徑與名稱 **/P**編譯器選項。|

## <a name="remarks"></a>備註

使用 **/Fi**編譯器選項，搭配 **/P**編譯器選項。

如果您指定的路徑`pathname`參數，原始程式檔的基底名稱做為前置處理過的輸出檔的基底名稱。 `pathname`參數不需要特定的副檔名。 不過，如果您未指定副檔名，會使用 「.i 」 的延伸模組。

## <a name="example"></a>範例

下列命令列 PROGRAM.cpp 會前置處理，會保留註解，新增[#line](../../preprocessor/hash-line-directive-c-cpp.md)指示詞，並將結果寫入 MYPROCESS.i 檔案。

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>另請參閱

[編譯器選項](../../build/reference/compiler-options.md)<br/>
[/P (前置處理至檔案)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[指定路徑名稱](../../build/reference/specifying-the-pathname.md)