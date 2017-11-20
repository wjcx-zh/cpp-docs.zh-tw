---
title: "如何： 建立資源指令碼檔 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8521849ab71f05b10dc8d3b861c93ba71b552eb4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-create-a-resource-script-file"></a>如何：建立資源指令碼檔
> [!NOTE]
>  資源編輯器在 Express 版中無法使用。  
>   
>  這份資料適用於 Windows 桌面應用程式。 以 .NET 語言撰寫的專案不會使用資源指令碼檔。 如需詳細資訊，請參閱 [資源檔](../windows/resource-files-visual-studio.md)。  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>建立新的資源指令碼 (.rc) 檔  
  
1.  將焦點放在 `Solution Explorer`中的現有專案資料夾中，例如 "MyProject"。  
  
    > [!NOTE]
    >  請勿混淆方案總管中的專案資料夾與方案資料夾。 如果您將焦點放在方案資料夾中，您在 [加入新項目]  對話方塊 (步驟 3) 中的選擇將會不同。  
  
2.  在 [專案]  功能表中，按一下 [加入新項目] 。  
  
3.  在 [加入新項目]  對話方塊中，按一下 [Visual C++]  資料夾，然後選擇右窗格中的 [資源檔 (.rc)]  。  
  
4.  在 [名稱]  文字方塊中提供資源指令碼檔的名稱，然後按一下 [開啟] 。  
  
 您現在可以 [建立](../windows/how-to-create-a-resource.md) 新的資源並加入 .rc 檔中。  
  
> [!NOTE]
>  您只能將資源指令碼 (.rc 檔) 加入已載入 Visual Studio IDE 的現有專案中， 而不能建立獨立的 .rc 檔 (即專案以外的檔案)。 [資源範本](../windows/how-to-use-resource-templates.md) (.rct 檔) 則可以隨時建立。  
  
 RRequirements  
  
 Win32  
  
## <a name="see-also"></a>另請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)