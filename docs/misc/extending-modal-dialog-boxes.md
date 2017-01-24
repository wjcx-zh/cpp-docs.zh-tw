---
title: "擴充強制回應對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio 擴充功能中的強制回應對話方塊"
  - "Visual Studio 擴充功能, 強制回應對話方塊"
ms.assetid: 478743dc-9fd9-46d7-9739-859fb8841a4f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 擴充強制回應對話方塊
若要保證與 Visual Studio 的功能和視覺相容性，請建立 Visual Studio 擴充功能的強制回應對話方塊，方法是從 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> 物件衍生對話方塊視窗。 以這種方式衍生的對話方塊也可以提供其他功能；例如，您可以設定 F1 說明目標，以及啟用視窗的最小化和最大化。  
  
## 建立強制回應對話方塊  
  
1.  在您的專案中，加入 System.XAML 的參考。  
  
2.  在**方案總管** 中，以滑鼠右鍵按一下專案，然後按一下 \[加入\]，再按一下 \[視窗\]。  
  
3.  提供視窗的名稱，然後按一下 \[加入\]。  
  
     空的 XAML 視窗隨即出現在設計工具中。  
  
4.  在最上層 `Window` 項目中，加入 <xref:Microsoft.VisualStudio.PlatformUI> 的命名空間宣告，並將 `Window` 項目變更為 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> 項目，如下列範例所示。  
  
     [!code-xml[VSModalDialog#02](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_1.xaml)]  
  
5.  從 \[工具箱\] 中加入按鈕、標籤和其他控制項，並輸入文字標籤，然後調整對話方塊的外觀。  
  
6.  切換至程式碼檢視。  
  
7.  在類別定義中，設定要繼承自 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> 的類別 。 \(根據預設，類別繼承自 <xref:System.Windows.Window?displayProperty=fullName>\)。  
  
8.  加入按鈕和其他控制項的事件處理常式。  
  
#### 在強制回應對話方塊中加入 F1 說明  
  
1.  針對建構函式，加入接受字串作為其引數的參數，並使用相同的參數來設定建構函式繼承自基底建構函式，如下列範例所示。  
  
     [!code-cs[VSModalDialog#12](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_2.cs)]  
  
     這個建構函式將 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> 屬性設定為 `true`，並在使用者按 F1 或按一下 \[說明\] 按鈕時，將接收到的字串當成關鍵字使用。  
  
#### 在強制回應對話方塊中加入最小化和最大化按鈕  
  
1.  在建構函式中，將 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasMinimizeButton%2A> 和 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasHMaximizeButton%2A> 屬性設定為 `true`，如下列範例所示。  
  
     [!code-cs[VSModalDialog#13](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_3.cs)]  
  
    > [!WARNING]
    >  顯示 \[最小化\] 和 \[最大化\] 按鈕時，會隱藏 \[說明\] 按鈕，即使 <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> 屬性設定為 `true` 也是一樣。  
  
## 範例  
 下列範例示範具有兩個建構函式的強制回應對話方塊。 第一個建構函式接受 F1 關鍵字作為引數，並顯示 \[說明\] 按鈕。 第二個建構函式未接受任何引數，但會顯示 \[最小化\] 和 \[最大化\] 按鈕。 當您按一下 \[是\] 按鈕時，會叫用對話方塊的第二個執行個體，並啟用 \[說明\]。  
  
 [!code-xml[VSModalDialog#01](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_4.xaml)]  
  
 [!code-cs[VSModalDialog#11](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_5.cs)]  
  
 下列程式碼會從事件處理常式叫用對話方塊。  
  
 [!code-cs[VSModalDialog#21](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_6.cs)]  
  
## 請參閱  
 [建立和管理強制回應對話方塊](../Topic/Creating%20and%20Managing%20Modal%20Dialog%20Boxes.md)