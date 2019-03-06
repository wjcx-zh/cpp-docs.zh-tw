---
title: /APPCONTAINER
ms.date: 11/04/2016
f1_keywords:
- /APPCONTAINER
helpviewer_keywords:
- APPCONTAINER editbin option
- -APPCONTAINER editbin option
- /APPCONTAINER editbin option
ms.assetid: 0ca4f1ec-c8de-4a37-b3e2-deda7af0bb88
ms.openlocfilehash: ad451f5900841abe3f0fe10ae99fa0183e14e5c5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412585"
---
# <a name="appcontainer"></a>/APPCONTAINER

標記必須在應用程式容器中執行的可執行檔 — 比方說，Microsoft Store 或通用 Windows 應用程式。

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>備註

已設定 **/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 Microsoft Store 和通用 Windows 應用程式，必須設定這個選項。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)<br/>
[通用 Windows 應用程式是什麼？](/windows/uwp/get-started/universal-application-platform-guide)
