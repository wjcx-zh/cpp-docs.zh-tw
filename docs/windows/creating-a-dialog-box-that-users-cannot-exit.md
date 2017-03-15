---
title: "Creating a Dialog Box That Users Cannot Exit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "dialog boxes, creating"
  - "modal dialog boxes, logon screens"
  - "logon screens"
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Creating a Dialog Box That Users Cannot Exit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以建立使用者無法結束的執行階段對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。  
  
### 建立使用者無法結束的對話方塊  
  
1.  在對話方塊的 \[屬性\] 窗格中，將 \[系統功能表\] 屬性設為 \[false\]。  
  
     這會停用對話方塊系統功能表並 \[關閉\] 按鈕。  
  
2.  在對話方塊表單中，刪除 \[取消\] 和 \[確定\] 按鈕。  
  
     在執行階段，使用者無法結束具有下列特性的強制回應對話方塊。  
  
 若要啟用這類對話方塊的測試，測試對話方塊函式在按下 ESC 鍵時就偵測到。 \(Esc 鍵也稱為 VK\_ESCAPE 虛擬按鍵\)。 不論對話方塊設計的執行階段行為如何，您都可以在測試模式中按下 ESC 鍵終止它。  
  
> [!NOTE]
>  針對 MFC 應用程式建立使用者無法結束的對話方塊，您必須覆寫 `OnOK` 和 `OnCancel` 的預設行為；因為，即使刪除相關聯的按鈕，還是可以按 ENTER 或 ESC 鍵關閉對話方塊。  
  
 如需如何將資源加入 Managed 專案中的相關資訊，請參閱[桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
## 需求  
 Win32  
  
## 請參閱  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)