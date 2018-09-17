---
title: -範圍 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e7525b8c1872616182141d624bff8f94571952
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712188"
---
# <a name="range"></a>/RANGE

修改當搭配其他 dumpbin 選項，例如 /RAWDATA 或 /DISASM dumpbin 的輸出。

## <a name="syntax"></a>語法

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>參數

*vaMin*<br/>
要開始 dumpbin 操作虛擬位址。

*vaMax*<br/>
（選擇性）要結束 dumpbin 操作虛擬位址。 如果未指定，dumpbin 將會移至檔案結尾。

## <a name="remarks"></a>備註

若要查看映像的虛擬位址，請使用對應檔映像 （RVA + 基底）， **/DISASM**或是 **/HEADERS** dumpbin 或反組譯碼視窗的 Visual Studio 偵錯工具中的選項。

## <a name="example"></a>範例

在此範例中， **/範圍**用來修改顯示 **/disasm**選項。 在此範例中，以十進位數字表示的起始值，並結束值指定為十六進位的數字。

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)