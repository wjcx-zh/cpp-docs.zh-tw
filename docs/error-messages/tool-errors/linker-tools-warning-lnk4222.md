---
title: 連結器工具警告 LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: 52a4fee532eb9997dcf013f95246b27fdffc4c20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563094"
---
# <a name="linker-tools-warning-lnk4222"></a>連結器工具警告 LNK4222

匯出的符號 'symbol' 不可指派序數

不應該依序數匯出下列符號：

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

這些函式一定會位於依名稱、 使用`GetProcAddress`。 連結器警告這種匯出是因為它可能會導致較大的影像。 如果您序數匯出的範圍很大，而相對較少的匯出，則會發生此問題。 例如，套用至物件的

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

將會需要 100 個位置其中 98 匯出位址資料表中 (2-99) 只填滿。 相反地，

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

將需要兩個位置。 (請注意，您也可以匯出與[/匯出](../../build/reference/export-exports-a-function.md)連結器選項。)