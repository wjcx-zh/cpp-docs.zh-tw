---
title: "如何：建立使用 Windows Forms 的 [工具箱] 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "工具箱控制項"
  - "winforms"
  - "工具箱"
ms.assetid: abbd3c3c-3a6e-4539-bd6c-a5891dead234
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# 如何：建立使用 Windows Forms 的 [工具箱] 控制項
隨附於 [!INCLUDE[vssdk_dev11_long](../misc/includes/vssdk_dev11_long_md.md)] 的 \[WPF 工具箱控制項\] 範本，可讓您建立在安裝擴充功能時會自動加入 \[工具箱\] 的 Windows Forms 控制項。 本主題會示範如何使用範本建立可散發給其他使用者的 \[工具箱\] 控制項。  
  
> [!NOTE]
>  若要了解如何下載 Visual Studio SDK，請參閱 MSDN 網站上的 [Visual Studio 擴充性開發人員中心](http://go.microsoft.com/fwlink/?linkid=121964)。  
  
## 建立 \[工具箱\] 控制項  
 請使用 \[Windows Forms 工具箱控制項\] 範本建立專案，然後在設計工具中建置使用者介面 \(UI\)。  
  
#### 建立 \[Windows Forms 工具箱控制項\] 專案  
  
1.  按一下 \[**檔案**\] 功能表上的 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[新增專案\] 對話方塊的 \[已安裝的範本\] 下，按一下您慣用的程式設計語言節點，然後按一下 \[擴充性\]。 在專案類型清單中選取 \[Windows Forms 工具箱控制項\]。  
  
3.  在 \[名稱\] 方塊中，輸入專案要使用的名稱。 按一下 \[**確定**\]。  
  
     Visual Studio 會建立一個解決方案，包含使用者控制項、將控制項放入 \[工具箱\] 的屬性，和用於部署的 VSIX 資訊清單。  
  
#### 建置控制項 UI  
  
1.  在**方案總管**中按兩下 \[ToolboxControl.cs\] 在設計工具中開啟它。  
  
2.  從 \[工具箱\] 中將任何您想要的控制項拖曳至設計介面，根據您的設計排列它們。  
  
3.  在 \[屬性\] 視窗中，設定使用者控制項和子控制項上的公用屬性。  
  
## 編碼控制項  
 您的控制項預設會出現在 \[工具箱\] 中，當做和解決方案同名之 \[工具箱\] 項目群組的 **ToolboxControl1**。 您可以在 ToolboxControl.cs 檔案中變更這些名稱。  
  
#### 編碼控制項  
  
1.  在**方案總管**中，以滑鼠右鍵按一下 \[ToolboxControl.cs\]，然後按一下 \[檢視程式碼\] 在程式碼檢視中開啟檔案。  
  
2.  在實作控制項的部分類別的定義上，以滑鼠右鍵按一下類別名稱，再依序按一下 \[重構\] 和 \[重新命名\]。 將類別名稱變更為 \[工具箱\] 在安裝控制項時要顯示的名稱。  
  
3.  在類別定義正上方的 `ProvideToolboxControl` 屬性宣告中，將第一個參數的值變更為主控 \[工具箱\] 控制項的項目群組名稱。  
  
     下例會顯示 `General` 項目群組中之 `Counter` 控制項的 `ProvideToolboxControl` 屬性和調整過的類別定義。  
  
     [!code-cs[ToolboxControlWinForms#07](../misc/codesnippet/CSharp/how-to-create-a-toolbox-control-that-uses-windows-forms_1.cs)]  
  
4.  實作控制項的屬性、方法和事件。  
  
## 建置、測試和部署  
 按 F5 建置專案並可納入 .vsix 部署檔案，然後開啟在 \[工具箱\] 中安裝了控制項的 Visual Studio 的第二個執行個體。  
  
#### 建置和測試控制項  
  
1.  按 F5。  
  
2.  在 Visual Studio 的新執行個體中建立 Windows Forms 應用程式專案。  
  
3.  在 \[工具箱\] 中尋找控制項，並將它拖曳至設計介面。  
  
4.  在 \[屬性\] 視窗中確認屬性是否如預期出現。  
  
5.  加入測試方法和事件所需要的任何程式碼或其他控制項。  
  
6.  按 F5 鍵開啟 Windows Forms 應用程式。  
  
7.  請確認控制項的屬性、方法和事件如預期般運作。  
  
#### 部署內容  
  
1.  建置測試專案之後，在檔案總管中開啟專案的 \\bin\\debug\\ 資料夾，並找出 .vsix 檔案。  
  
2.  將 .vsix 檔案上傳到網路或網站。  
  
     如果將檔案上傳到 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkID=123847) 網站，其他使用者就可以使用 Visual Studio 的 \[擴充管理員\] 尋找並安裝控制項。  
  
## 請參閱  
 [建立 WPF 工具箱控制項](../Topic/Creating%20a%20WPF%20Toolbox%20Control.md)