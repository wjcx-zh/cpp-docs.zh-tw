---
title: 建立資源專用 DLL |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8ea6590a57a336740be0a9439c959ebe32239d4e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703453"
---
# <a name="creating-a-resource-only-dll"></a>建立僅含資源的 DLL

資源專用 DLL 是包含資源，例如圖示、 點陣圖、 字串和對話方塊而不是包含的 DLL。 使用資源專用 DLL 是共用相同的多個程式間的資源集的好方法。 它也會提供多種語言的當地語系化資源的應用程式的好方法 (請參閱[MFC 應用程式中的當地語系化資源： 附屬 Dll](../build/localized-resources-in-mfc-applications-satellite-dlls.md))。

若要建立資源專用 DLL 時，您會建立新的 (非 MFC) 的 Win32 DLL 專案，並將您的資源新增至專案。

- 選取 Win32 專案中**新的專案**對話方塊方塊，然後在 Win32 專案精靈 中指定 DLL 專案類型。

- Dll 中建立新的資源指令碼，其中包含的資源 （例如字串或功能表） 並儲存.rc 檔。

- 在 [**專案**] 功能表中，按一下**加入現有項目**，然後再將新的.rc 檔插入專案。

- 指定[/NOENTRY](../build/reference/noentry-no-entry-point.md)連結器選項。 /NOENTRY 可防止連結器連結參考`_main`dll，需要這個選項來建立僅含資源的 DLL。

- 建置 DLL。

使用資源專用 DLL 的應用程式應該呼叫[LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)明確地連結至 DLL。 若要存取資源，呼叫泛型函式`FindResource`和`LoadResource`，作用於任何種類的資源，或呼叫其中一個下列資源特有的函式：

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

應用程式應該呼叫`FreeLibrary`完成時使用的資源。

## <a name="see-also"></a>另請參閱

[使用資源檔](../windows/working-with-resource-files.md)<br/>
[Visual C++ 中的 DLL](../build/dlls-in-visual-cpp.md)