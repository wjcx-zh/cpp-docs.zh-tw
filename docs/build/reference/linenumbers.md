---
title: /LINENUMBERS
ms.date: 11/04/2016
f1_keywords:
- /linenumbers
helpviewer_keywords:
- LINENUMBERS dumpbin option
- line numbers
- -LINENUMBERS dumpbin option
- /LINENUMBERS dumpbin option
ms.assetid: 1681d582-2c2f-484e-9920-109959549055
ms.openlocfilehash: aec21026ded821f9a87e7c0c2aeefd13a927a401
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417303"
---
# <a name="linenumbers"></a>/LINENUMBERS

```
/LINENUMBERS
```

## <a name="remarks"></a>備註

此選項會顯示 COFF 行號。 行號存在目的檔中，如果它已編譯程式資料庫 (/Zi)，C7 相容 (/ Z7)，或僅行數 (/Zd)。 可執行檔或 DLL 包含 COFF 行號如果它已與產生偵錯資訊連結 (/debug)。

只有[/HEADERS](../../build/reference/headers.md) DUMPBIN 選項只適用於所產生的檔案上[/GL](../../build/reference/gl-whole-program-optimization.md)編譯器選項。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)
