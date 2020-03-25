---
title: 連結器工具警告 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183029"
---
# <a name="linker-tools-warning-lnk4222"></a>連結器工具警告 LNK4222

匯出的符號 ' symbol ' 不應指派序數

下列符號不應由序數匯出：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

這些函式一律以名稱定位，使用 `GetProcAddress`。 連結器會警告這種匯出，是因為它可能會產生較大的影像。 如果您的序數匯出範圍較少量的匯出，就會發生這種情況。 例如，

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

在匯出位址資料表中，將會需要100個位置，其中包含98個（2-99）。 另一方面

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

將需要兩個位置。 （請注意，您也可以使用[/export](../../build/reference/export-exports-a-function.md)連結器選項來匯出）。
