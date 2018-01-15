---
title: "如何： 使用資源範本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- language-specific template files
- resource templates
- resources [Visual Studio], creating
- rct files
- templates, resource templates
- resources [Visual Studio], templates
- .rct files
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9bace4f6d8835d9aece7679fa1bb89af3d7a20ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-resource-templates"></a>如何：使用資源範本
資源範本是您已儲存為 .rct 檔案的自訂資源。 資源範本之後可以做為建立其他資源的起點。 資源範本可節省在開發共用功能的其他資源或資源群組的時間，例如標準控制項和其他重複的項目。 例如，您可能想要在數個對話方塊中包含 [說明] 按鈕和公司標誌的圖示。 若要快速地執行，請建立新對話方塊範本並使用標誌與 [說明] 按鈕加以自訂。  
  
 一旦自訂資源範本之後，您必須將您的變更儲存在範本資料夾 （或 include 路徑中指定的任何位置），讓新的資源範本出現在 [資源類型下[加入資源對話方塊](../windows/add-resource-dialog-box.md). 然後您可以視需要經常使用新資源範本。  
  
> [!NOTE]
>  您可以將特定語言的範本檔置於主要範本目錄的子目錄中。 比方說，您可以在其中放置英文版的範本檔案\\< 資源範本目錄\>\1033。  
  
### <a name="to-create-a-template-for-resources"></a>建立資源的範本  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下您的專案。  
  
2.  從捷徑功能表，選擇 [**新增**，然後按一下 [**加入新項目**。  
  
3.  在**加入新項目**對話方塊中，於**範本：** ] 窗格中，選擇**資源範本檔 (.rct)**。  
  
4.  提供的名稱和新的.rct 檔案的位置，然後按**開啟**。  
  
5.  新的.rct 檔案會加入至您的專案，並會出現在 [方案總管] 底下**資源**資料夾。  
  
     您現在可以按兩下.rct 檔案，在文件視窗中開啟它，然後將資源新增至它 (文件視窗中的檔案上按一下滑鼠右鍵，然後選擇 [**加入資源**從快顯功能表)。 然後，您可以自訂這些資源，並儲存 .rct 檔案。  
  
    > [!NOTE]
    >  當您建立新 RCT 檔案時，Visual Studio 內，搜尋其 \Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates，\Program Files\Microsoft Visual Studio 9.0\VC\VCResourceTemplates\\*LCID* (例如 1033 代表英文)*或*上的任何位置[include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如果您偏好要將 RCT 檔案儲存在另一個檔案資料夾，例如 \我的文件，您只需要將此資料夾加入至 include 路徑，Visual Studio 將會找到您的 RCT 檔案。  
  
### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>將現有的 .rc 檔轉換成 .rct 檔案  
  
1.  [開啟.rc 檔，為獨立檔案](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
2.  在**檔案**功能表上，按一下 [ **儲存\<*您的檔案名稱*> 做為 * *。  
  
3.  指定的位置，然後按一下**確定**。  
  
### <a name="to-create-a-new-resource-from-a-template"></a>從範本建立新資源  
  
1.  在[資源檢視](../windows/resource-view-window.md)] 窗格中，以滑鼠右鍵按一下.rc 檔，然後選擇**加入資源**從捷徑功能表。  
  
2.  在**加入資源**對話方塊方塊中，按一下加號 (**+**) 旁邊的展開資源節點，並查看所有可用該資源的範本資源。  
  
3.  按兩下您想要使用的範本。  
  
4.  在資源編輯器中視需要修改所加入的資源。  
  
     資源編輯器會自動提供唯一的資源識別碼。 您可以修訂[資源內容](../windows/changing-the-properties-of-a-resource.md)視。  
  
 如需將資源加入至 managed 專案的詳細資訊，請參閱[桌面應用程式中的資源](/dotnet/framework/resources/index)中*.NET Framework 開發人員手冊 》。*  
  
 需求  
  
 Win32  
  
## <a name="see-also"></a>請參閱  
 [資源檔](../windows/resource-files-visual-studio.md)   
 [資源編輯器](../windows/resource-editors.md)