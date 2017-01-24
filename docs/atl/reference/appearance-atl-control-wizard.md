---
title: "外觀, ATL 控制項精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.control.misc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控制項精靈, 外觀"
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 外觀, ATL 控制項精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在這裡插入「搜尋結果」摘要。  
  
 使用這個精靈頁面來識別控制項的其他使用者項目選項。  在[選項, ATL 控制項精靈](../../atl/reference/options-atl-control-wizard.md)頁面的 \[**控制項型別**\] 下，視為 \[**標準控制項**\] 的控制項可以使用這個頁面。  
  
## UIElement 清單  
 **檢視狀態**  
 設定容器內控制項的外觀。  
  
-   \[**不透明**\]：設定 [VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201) 列舉型別中的 `VIEWSTATUS_OPAQUE` 位元，並繪製傳遞至 [CComControlBase::OnDraw](../Topic/CComControlBase::OnDraw.md) 方法的整個控制項矩形。  控制項會變得完全不透明，而控制項界限外不會出現任何容器。  
  
     這個設定能幫助加速容器繪製控制項的速度。  如果未選取這個選項，則控制項會包含透明部分。  
  
     只有不透明控制項才能具有純色背景 \(Background\)。  
  
-   設定在 `VIEWSTATUS` 列舉型別中的 `VIEWSTATUS_SOLIDBKGND` 位元。  控制項的背景將變成無圖樣的純色。  
  
     只有在同時選取 \[**不透明**\] 選項的情況下，才能使用這個選項。  
  
 **加入的控制項將依據**  
 藉由將 [CContainedWindow](../Topic/CContainedWindow.md) 資料成員加入至實作控制項的類別，將控制項設定為以 Windows 控制項型別為基礎。  它也可加入訊息對應 \(Message Map\) 和訊息處理常式 \(Message Handler\) 函式來為控制項處理 Windows 訊息。  請從以下清單選擇您要建立 Windows 控制項的類型：  
  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **其他狀態**  
 設定控制項的其他外觀和行為選項。  
  
-   \[**執行階段不可見**\]：將控制項設定為在執行階段不可見。  您可使用不可見的控制項於背景執行作業，例如在固定的時間間隔引發事件。  
  
-   \[**動作和按鈕相同**\]：設定 [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) 列舉型別中的 `OLEMISC_ACTSLIKEBUTTON` 字元，啟用控制項使其動作和按鈕相同。  如果容器將控制項的用戶端站台標記為預設按鈕，則選取這個選項會讓您的按鈕控制項以較粗的框架 \(Frame\) 繪製其本身，並做為預設按鈕。  如需詳細資訊，請參閱 [CComControlBase::GetAmbientDisplayAsDefault](../Topic/CComControlBase::GetAmbientDisplayAsDefault.md)。  
  
-   \[**動作和標籤相同**\]：設定 `OLEMISC` 列舉型別中的 `OLEMISC_ACTSLIKELABEL` 位元，啟用控制項來取代容器的原生 \(Native\) 標籤。  必要時容器會決定如何處理這個旗標。  
  
 **其他**  
 設定控制項的其他行為選項。  
  
-   \[**正規化的 DC**\]：設定在呼叫控制項來繪製其本身時，建立正規化的裝置內容。  這個動作會標準化控制項的外觀，但會讓繪製效率較低。  
  
-   \[**僅限視窗**\]：指定您的控制項不能為無視窗 \(Windowless\) 控制項。  如果您不選取這個選項，您的控制項在支援無視窗物件的容器中會自動成為無視窗控制項，而在不支援無視窗物件的容器中會自動成為視窗型控制項。  選取這個選項會強制將您的控制項設為視窗型控制項，即使在支援無視窗物件的容器中也一樣。  
  
-   \[**可插入的**\]：選取這個選項來讓您的控制項出現在如 Word 和 Excel 等應用程式的 \[**插入物件**\] 對話方塊中。  任何有支援內嵌物件 \(Embedded Object\) 的應用程式都可透過這個對話方塊來插入您的控制項。  
  
## 請參閱  
 [ATL 控制項精靈](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT Sample: Superclasses a Standard Windows Control](http://msdn.microsoft.com/zh-tw/30e46bdc-ed92-417c-b6b8-359017265a7b)