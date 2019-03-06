---
title: 環境變數巨集
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, environment variable macros
- environment variables, macros in NMAKE
- macros, environment-variable
ms.assetid: f8e96635-0906-47b0-9f56-12a6fdf5e347
ms.openlocfilehash: baca09fbf93679b767a1de5d0553eb7462f31e4f
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417667"
---
# <a name="environment-variable-macros"></a>環境變數巨集

NMAKE 繼承巨集定義的工作階段開始之前就存在的環境變數。 如果作業系統環境中設定變數，它位於與 NMAKE 巨集。 繼承的名稱會轉換成大寫。 前置處理早繼承。 您可以使用 [/E] 選項，讓繼承自環境變數，以覆寫具有相同名稱的 makefile 中的任何巨集的巨集。

工作階段中，可以重新定義環境變數巨集，而這會變更對應的環境變數。 您也可以變更利用 SET 命令的環境變數。 若要變更環境變數的工作階段中使用 SET 命令不會變更對應的巨集，不過。

例如: 

```
PATH=$(PATH);\nonesuch

all:
    echo %PATH%
```

在此範例中，變更`PATH`變更對應的環境變數`PATH`; 它會將附加`\nonesuch`至您的路徑。

如果環境變數定義為字串，會是 makefile 中語法不正確，會建立沒有巨集，並不會產生警告。 如果變數的值包含貨幣符號 （$），則 NMAKE 會將它解譯為開頭的巨集引動過程。 使用巨集，可能會導致非預期的行為。

## <a name="see-also"></a>另請參閱

[特殊的 NMAKE 巨集](../build/special-nmake-macros.md)
