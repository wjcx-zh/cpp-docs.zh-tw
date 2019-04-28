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
ms.openlocfilehash: eb922a29b00fee63effae302505f25c98b04523e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274023"
---
# <a name="appcontainer"></a>/APPCONTAINER

標記必須在應用程式容器中執行的可執行檔 — 比方說，Microsoft Store 或通用 Windows 應用程式。

```

/APPCONTAINER[:NO]
```

## <a name="remarks"></a>備註

已設定 **/APPCONTAINER** 選項的可執行檔只能在應用程式容器中執行，這是在 Windows 8 中引進的處理序隔離環境。 Microsoft Store 和通用 Windows 應用程式，必須設定這個選項。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)<br/>
[通用 Windows 應用程式是什麼？](/windows/uwp/get-started/universal-application-platform-guide)
