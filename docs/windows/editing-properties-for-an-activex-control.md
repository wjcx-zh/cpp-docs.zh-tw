---
title: 編輯 ActiveX 控制項的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], editing properties
- ActiveX controls [C++], properties
ms.assetid: e5880c62-36c7-4701-bc99-97a82974c22a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f64fd94eca03b132d0448147085b04e3ff6c1097
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648057"
---
# <a name="editing-properties-for-an-activex-control"></a>編輯 ActiveX 控制項的屬性
獨立廠商所提供的 ActiveX 控制項可能都配有其自己的屬性和特性的。 適用於 ActiveX 控制項的屬性會顯示在**屬性**視窗。 此外，ActiveX 控制項的寫入器所建立的任何屬性頁面會顯示在**屬性頁** 對話方塊 (若要檢視 **屬性頁**對於特定的 ActiveX 控制項中，按一下 [ **屬性頁**按鈕[屬性] 視窗](/visualstudio/ide/reference/properties-window))。  
  
 各種索引標籤會顯示在屬性頁面中的 ActiveX 控制項，視屬性工作表做為 ActiveX 控制項的一部分，而定。  
  
> [!NOTE]
>  下列程序適用於使用屬性頁編輯 ActiveX 控制項。 您也可以瀏覽並編輯 ActiveX 屬性中的新**屬性**視窗。  
  
### <a name="to-edit-properties-for-an-activex-control"></a>若要編輯 ActiveX 控制項的屬性  
  
1.  選取 **ActiveX**控制項。  
  
2.  在上**檢視** 功能表中，按一下**屬性頁**檢視內容。  
  
3.  視需要在 [屬性] 頁面中，請進行變更。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [檢視及加入 ActiveX 控制項加入對話方塊](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)   
 [在對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)   
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)