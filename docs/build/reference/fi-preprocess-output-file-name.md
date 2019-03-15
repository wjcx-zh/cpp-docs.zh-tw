---
title: /Fi (前置處理輸出檔名稱)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 990c48a72c3f6017d893ddf9b46bcbb737bfb634
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820191"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (前置處理輸出檔名稱)

指定輸出檔名稱[/P （前置處理至檔案）](p-preprocess-to-a-file.md)編譯器選項會將前置處理過的輸出。

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

[MSVC 編譯器選項](compiler-options.md)<br/>
[/P (前置處理至檔案)](p-preprocess-to-a-file.md)<br/>
[指定路徑名稱](specifying-the-pathname.md)
