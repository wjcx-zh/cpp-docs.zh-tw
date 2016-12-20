---
title: "設定色彩、漸層和不透明度 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "UI 項目設計 [Visual Studio SDK]"
ms.assetid: 1734bdc7-5e16-46c7-8507-eef5cea75cb9
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# 設定色彩、漸層和不透明度
Visual Studio 中的所有使用者介面 \(UI\) 項目都是在 Windows Presentation Foundation \(WPF\) 中建立。 因此，當您建立工具視窗或其他 UI 項目時，可以在這些項目上設定適當的屬性，來套用色彩、漸層和不透明度。 您可以使用 \[屬性\] 視窗將這些設成特定值，或是查詢整合式開發環境 \(IDE\) 以取得系統值。 當您想要您的擴充功能類似於 IDE 的其餘部分時，我們建議您使用系統值。  
  
 仍然支援 Windows Forms UI 和原生程式碼 UI 以取得回溯相容性。 如需如何在非 WPF 擴充功能中設定色彩與漸層的相關資訊，請參閱 [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)] 文件。  
  
## 設定色彩、漸層和不透明度  
 您可以藉由設定 `Background`、`Foreground`、`Opacity` 或其他視覺屬性來變更大部分 XAML 項目的外觀。 這些屬性對應至接受 <xref:System.Windows.Media.Brush?displayProperty=fullName> 作為值的屬性。  
  
#### 在工具視窗中設定背景色彩、漸層和不透明度  
  
1.  開啟 MyControl.xaml。  
  
2.  在 \[XAML\] 窗格的最上層 <xref:System.Windows.Controls.UserControl> 項目中，輸入 `background=`。  
  
     IntelliSense 會顯示 BackGround 屬性的色彩清單。  
  
     從清單中選取色彩。  
  
3.  在 \[屬性\] 視窗中，展開 \[筆刷\] 節點，然後按一下 \[背景\]。  
  
     \[屬性\] 視窗會顯示色彩選擇器。 在色彩選擇器的上方，是一列代表筆刷的圖示。  
  
4.  使用滑桿來選擇色彩。  
  
     XAML 會立即更新以顯示新的背景色彩。  
  
5.  按一下漸層筆刷圖示。  
  
     色彩選擇器變更為漸層選擇器。  
  
6.  使用滑桿來選擇漸層。  
  
     XAML 會立即更新以顯示新的背景漸層。  
  
7.  按一下影像筆刷圖示。  
  
     漸層選擇器變更為影像選取工具。  
  
8.  選取影像並設定其自動縮放和並排顯示參數。  
  
     XAML 會立即更新以顯示新的背景影像。  
  
9. 按一下 Null 筆刷圖示。  
  
     設計工具中的背景會回到中性，且 `BackGround` 屬性會設為 `"{x:Null}"`。  
  
## 查詢系統值  
 您可以使用 <xref:Microsoft.VisualStudio.Shell.VsBrushes?displayProperty=fullName> 類別屬性查詢系統值，這些屬性會參考 Visual Studio 其他部分中所設定的筆刷。  
  
#### 藉由查詢系統值來設定色彩、漸層和不透明度  
  
1.  選取 XAML 項目。  
  
2.  在項目定義中，將項目的其中一個視覺屬性設為 `VsBrushes` 類別的屬性，如下列範例所示。  
  
     [!code-xml[TWShortcutMenu#32](../misc/codesnippet/Xaml/setting-colors-gradients-and-opacity_1.xaml)]  
  
     使用 [DynamicResource](../Topic/DynamicResource%20Markup%20Extension.md) 擴充功能可以視需要變更值，例如，當使用者變更設定時。 您必須使用 [x:Static](../Topic/x:Static%20Markup%20Extension.md) 擴充功能，因為 `VsBrushes` 類別不是預設 WPF 命名空間的一部分。  
  
## 請參閱  
 [擴充工具視窗](../misc/extending-tool-windows.md)