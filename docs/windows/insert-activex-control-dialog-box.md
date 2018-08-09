---
title: 插入 ActiveX 控制項對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0201619d463d677eae312d70a543a19887dbdb40
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011786"
---
# <a name="insert-activex-control-dialog-box"></a>插入 ActiveX 控制項對話方塊
此對話方塊可讓您[插入您的對話方塊中的 ActiveX 控制項](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md)使用時[對話方塊編輯器](../windows/dialog-editor.md)。  
  
### <a name="activex-control"></a>ActiveX 控制項 
 會顯示一份 Active X 控制項。 從這個對話方塊中插入控制項不會產生包裝函式類別。 如果您需要的包裝函數類別，使用[類別檢視](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925)若要建立一個 (如需詳細資訊，請參閱[加入類別](../ide/adding-a-class-visual-cpp.md))。 如果 Active X 控制項不會出現在這個對話方塊中，再次嘗試安裝控制項根據廠商的指示。  
  
### <a name="path"></a>路徑  
 顯示 ActiveX 控制項所在的檔案。  
  
 您可以放置在控制項**工具箱**視窗以方便存取。 如需詳細資訊，請參閱 <<c0> [ 自訂工具箱對話方塊](http://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 如需將資源加入 managed 專案的詳細資訊，請參閱[Resources in Desktop Apps](/dotnet/framework/resources/index)中 *.NET Framework 開發人員指南*。 如需手動將資源檔加入 managed 專案、 存取資源、 顯示靜態資源及指派資源字串給屬性的資訊，請參閱[建立桌面應用程式的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和當地語系化的受管理的應用程式中的資源上的資訊，請參閱[全球化和當地語系化.NET Framework 應用程式](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [工具箱、 對話方塊編輯器索引標籤](../windows/dialog-editor-tab-toolbox.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [對話方塊中的控制項](../windows/controls-in-dialog-boxes.md)