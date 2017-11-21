---
title: "建立使用者無法結束的對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes, creating
- modal dialog boxes, logon screens
- logon screens
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1992f896baac2748246e8c74ba3abbc2997a95af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-dialog-box-that-users-cannot-exit"></a>建立使用者無法結束的對話方塊
您可以建立使用者無法結束的執行階段對話方塊。 這種對話方塊對登入以及鎖定應用程式或文件非常實用。  
  
### <a name="to-create-a-dialog-box-that-a-user-cannot-exit"></a>建立使用者無法結束的對話方塊  
  
1.  在對話方塊的 [屬性]  窗格中，將 [系統功能表]  屬性設為 [false] 。  
  
     這會停用對話方塊系統功能表並 [關閉]  按鈕。  
  
2.  在對話方塊表單中，刪除 [取消]  和 [確定]  按鈕。  
  
     在執行階段，使用者無法結束具有下列特性的強制回應對話方塊。  
  
 若要啟用這類對話方塊的測試，測試對話方塊函式在按下 ESC 鍵時就偵測到。 (Esc 鍵也稱為 VK_ESCAPE 虛擬按鍵)。不論對話方塊設計的執行階段行為如何，您都可以在測試模式中按下 ESC 鍵終止它。  
  
> [!NOTE]
>  針對 MFC 應用程式建立使用者無法結束的對話方塊，您必須覆寫 `OnOK` 和 [確定] `OnCancel` 的預設行為；因為，即使刪除相關聯的按鈕，還是可以按 ENTER 或 ESC 鍵關閉對話方塊。  
  
 如需如何將資源加入至 managed 專案的資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)。  
  
## <a name="requirements"></a>需求  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [如何： 建立資源](../windows/how-to-create-a-resource.md)   
 [資源檔](../windows/resource-files-visual-studio.md)   
 [對話方塊編輯器](../windows/dialog-editor.md)

