---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299750"
---
# <a name="dependents"></a>/DEPENDENTS

傾印映射從中匯入函式的 Dll 名稱。 您可以使用清單來判斷要與您的應用程式一起轉散發的 Dll, 或尋找缺少的相依性名稱。

## <a name="syntax"></a>語法

> **/DEPENDENTS**

此選項適用于命令列上指定的所有可執行檔。 它不接受任何引數。

## <a name="remarks"></a>備註

**/DEPENDENTS**選項會加入影像將函式匯入輸出之來源 dll 的名稱。 此選項不會傾印匯入函式的名稱。 若要查看已匯入函式的名稱, 請使用[/IMPORTS](imports-dumpbin.md)選項。

只有 [/HEADERS](headers.md) DUMPBIN 選項可用於以 [/GL](gl-whole-program-optimization.md) 編譯器選項產生的檔案上。

## <a name="example"></a>範例

這個範例會顯示內[建的用戶端可執行檔之 **/DEPENDENTS**選項的 DUMPBIN 輸出:建立並使用您自己的動態連結](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)庫:

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
