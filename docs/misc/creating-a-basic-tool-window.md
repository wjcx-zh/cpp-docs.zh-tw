---
title: "建立基本工具視窗 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, 工具視窗"
  - "工具視窗, 在 IDE 中建立"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 建立基本工具視窗
工具視窗是 Visual Studio 的通用項目：**方案總管**、\[工作清單\]、\[錯誤清單\] 和 \[輸出\] 視窗全部都是工具視窗。 所有工具視窗都可以透過相同的方式停駐在 IDE 中。 可預測的停駐讓使用者能夠有效率地管理其工作和資訊。  
  
 Visual Studio Package 範本可建立簡單工具視窗的基本實作。  
  
### 使用 Visual Studio Package 範本建立工具視窗  
  
1.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
2.  在 \[新增專案\] 對話方塊中，展開 \[其他專案類型\]，然後按一下 \[擴充性\]。  
  
3.  在 \[範本\] 窗格中，按一下 \[Visual Studio 封裝\]。  
  
4.  在 \[位置\] 方塊中，輸入 VSPackage 的檔案路徑。  
  
5.  在 \[名稱\] 方塊中，輸入方案的名稱，然後按一下 \[確定\] 啟動範本。  
  
6.  在 \[選取程式設計語言\] 頁面上，選取 C\# 或 Visual Basic。 讓範本產生 key.snk 檔案以簽署組件。 或者，**瀏覽**至您自己的金鑰檔。 範本會複製您的金鑰檔並將其命名為 key.snk。  
  
7.  在 \[基本 VSPackage 資訊\] 頁面上，指定有關 VSPackage 的任何詳細資料，或是接受預設值。 如需詳細資訊，請參閱[逐步解說：使用 Visual Studio 封裝範本建立功能表命令](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md)。  
  
8.  在 \[選取 VSPackage 選項\] 頁面上，核取 \[工具視窗\]。  
  
9. 在 \[工具視窗選項\] 頁面的 \[視窗名稱\] 方塊中，輸入標題列的名稱。 這個名稱也會當做工具視窗中功能表命令的顯示文字來使用。 此功能表命令會新增至 \[檢視\] 功能表的 \[其他視窗\] 子功能表。 在 \[命令 ID\] 方塊中，輸入工具視窗的命令 ID，或是接受預設值。  
  
10. 按一下 \[完成\]，在您指定的資料夾中建立 VSPackage。  
  
### 測試工具視窗  
  
1.  指向 \[檢視\] 功能表中的 \[其他視窗\]，然後按一下您的工具視窗命令。 工具視窗與 \[按這裡\!\] 按鈕隨即出現。  
  
2.  按一下按鈕。 這會顯示一則內含下列文字的訊息：  
  
     目前位於 \[Company.\<VSPackage 名稱\>.MyControl\].button1\_Click\(\) 中。  
  
## 請參閱  
 [以程式設計方式開啟工具視窗](../misc/opening-a-tool-window-programmatically.md)   
 [VSPackage 基本資訊](../misc/vspackage-essentials.md)