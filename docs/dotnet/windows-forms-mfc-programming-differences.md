---
title: "Windows Form MFC 程式設計的差異 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 696e7684eb91abbf41e3f7a2e1df20b6fa7e5c17
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-formsmfc-programming-differences"></a>Windows Form/MFC 程式設計的差異
中的主題[在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)描述 Windows Form 的 MFC 支援。 如果您不熟悉.NET Framework 或 MFC 程式設計，本主題會提供程式設計的差異，兩者之間的背景資訊。  
  
 Windows Form 是建立在.NET Framework 上的 Microsoft Windows 應用程式。 這個架構會提供類別，可讓您用來開發豐富的 Windows 應用程式現代、 物件導向、 可延伸集。 使用 Windows Form，就可以建立的豐富型用戶端應用程式可以存取各種資料來源，並提供資料顯示和編輯資料的功能，使用 Windows Form 控制項。  
  
 不過，如果您是習慣於 MFC，您可能會用來建立特定類型的尚未明確支援 Windows Form 中的應用程式。 Windows Form 應用程式相當於 MFC 對話方塊應用程式。 不過，它們不提供以單一文件介面 (SDI)，多重文件介面 (MDI) 直接支援 OLE 文件伺服器/容器、 ActiveX 文件、 文件/檢視支援等其他 MFC 應用程式類型的基礎結構和多個最上層介面 (MTI)。 您可以撰寫您自己的邏輯來建立這些應用程式。  
  
 如需 Windows Forms 應用程式的詳細資訊，請參閱[簡介 Windows Form](/dotnet/framework/winforms/windows-forms-overview)。  
  
 顯示與 MFC 一起使用的 Windows Form 的範例應用程式，請參閱[MFC 和 Windows Form 整合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)。  
  
 MFC 檢視或文件，下列路由功能的命令在 Windows Form 沒有對等用法：  
  
-   整合式介面  
  
     Mfc 文件上按一下滑鼠右鍵並選取這類動詞命令為開啟、 編輯或列印時，會使用殼層的命令列引數與動態資料交換 (DDE) 命令。 Windows Form 任何殼層整合並不會回應殼層動詞命令。  
  
-   文件範本  
  
     在 MFC 中，文件範本會將包含在框架視窗 （在 MDI、 SDI 或 MTI 模式） 中，檢視與您所開啟的文件產生關聯。 Windows Form 有沒有相當於文件範本。  
  
-   文件  
  
     MFC 註冊文件的檔案類型，並在命令介面中開啟文件時處理的文件類型。 Windows Form 有任何文件支援。  
  
-   文件狀態  
  
     MFC 會維護文件的變更狀態。 因此，當您關閉應用程式、 關閉最後一個檢視，其中包含應用程式，或從 Windows 結束，MFC 會提示您儲存文件。 Windows Form 有沒有對等的支援。  
  
-   命令  
  
     MFC 會具有命令的概念。 功能表、 工具列和快顯功能表所有可以叫用相同的命令，例如剪下和複製。 Windows Form 中的命令是緊密繫結的事件，從特定的 UI 項目 （例如功能表項目）;因此，您必須明確地連接所有命令事件。 您也可以處理多個事件與 Windows Form 中的單一處理常式。 如需詳細資訊，請參閱[連接至 Windows Form 中的單一事件處理常式的多個事件](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms)。  
  
-   命令路由  
  
     MFC 命令路由，可讓使用中檢視或文件處理命令。 因為在同一個命令通常會有不同的意義不同的檢視 （例如，複製的行為以不同的方式比圖形編輯器中的文字編輯檢視中）、 命令需要作用中的檢視所處理。 Windows Form 功能表和工具列有沒有固有的了解使用中的檢視，因為您不能有不同的處理常式的每種檢視類型您**MenuItem.Click**事件，而不需要撰寫額外的內部程式碼。  
  
-   命令更新機制  
  
     MFC 會具有更新機制的命令。 因此，使用中檢視或文件會負責的 UI 項目 （例如，啟用或停用功能表項目、 工具列按鈕和核取狀態等等） 的狀態。 Windows Form 有沒有對等的命令更新機制。  
  
## <a name="see-also"></a>請參閱  
 [在 MFC 中使用 Windows Form 使用者控制項](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Forms 逐步解說](http://msdn.microsoft.com/en-us/fd44d13d-4733-416f-aefc-32592e59e5d9)