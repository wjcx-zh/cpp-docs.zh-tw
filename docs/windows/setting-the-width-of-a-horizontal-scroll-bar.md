---
title: 設定水平捲軸的寬度
ms.date: 11/04/2016
helpviewer_keywords:
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
ms.openlocfilehash: 393571b79d27485e840d150549208c899e8ed1d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625949"
---
# <a name="setting-the-width-of-a-horizontal-scroll-bar"></a>設定水平捲軸的寬度

當您使用 MFC 類別的對話方塊中新增具有水平捲軸的清單方塊時，捲軸不會自動出現在您的應用程式。

### <a name="to-make-the-scroll-bar-appear"></a>若要讓捲軸出現

1. 藉由呼叫設定的最寬的項目最大寬度[CListBox::SetHorizontalExtent](../mfc/reference/clistbox-class.md#sethorizontalextent)程式碼中。

   沒有設定這個值，捲軸不會出現，即使當清單方塊中的項目都超出 方塊中。

如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>需求

MFC

## <a name="see-also"></a>另請參閱

[對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)<br/>
[控制項](../mfc/controls-mfc.md)