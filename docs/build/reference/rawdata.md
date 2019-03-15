---
title: /RAWDATA
ms.date: 11/04/2016
f1_keywords:
- /rawdata
helpviewer_keywords:
- RAWDATA dumpbin option
- raw data
- -RAWDATA dumpbin option
- /RAWDATA dumpbin option
ms.assetid: 41cba845-5e1f-415e-9fe4-604a52235983
ms.openlocfilehash: 02af8df04d80c20c5d7629b51abab6295a21f5e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57816460"
---
# <a name="rawdata"></a>/RAWDATA

```
/RAWDATA[:{1|2|4|8|NONE[,number]]
```

## <a name="remarks"></a>備註

此選項會顯示每個區段的未經處理的內容檔案中。 引數來控制顯示的格式如下所示：

|引數|結果|
|--------------|------------|
|1|預設值。 如果它們有列印的表示，內容會顯示以十六進位位元組為單位，以及為 ASCII 字元。|
|2|內容會顯示為 2 個位元組的十六進位值。|
|4|內容會顯示為 4 個位元組的十六進位值。|
|8|內容會顯示為 8 個位元組的十六進位值。|
|NONE|隱藏未經處理資料。 這個引數是可用來控制輸出的所有 /。|
|*數字*|顯示的行都會設定為保留的寬度`number`每行的值。|

只有[/HEADERS](headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](dumpbin-options.md)
