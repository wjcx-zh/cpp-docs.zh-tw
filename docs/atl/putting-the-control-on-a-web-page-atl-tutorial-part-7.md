---
title: "將控制項放在網頁上 (ATL 教學課程，第 7 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 將控制項放在網頁上 (ATL 教學課程，第 7 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

現在您的控制項已完成。  若要查看控制項在實際情況中的運作方式，將它放在網頁上。  包含控制項的 HTML 檔會在您定義您的控制項時建立。  從 \[**方案總管**\] 開啟 PolyCtl.htm 檔案，您可以在網頁上看到您的控制項。  
  
 在這個步驟中，您將撰寫網頁的指令碼以回應事件。  您也會修改控制項，告知 Internet Explorer 該控制項是指令碼處理安全的。  
  
## 撰寫網頁指令碼  
 控制項還沒有執行任何動作，因此會變更網頁以回應您傳送的事件。  
  
#### 若要撰寫網頁指令碼  
  
1.  開啟 PolyCtl.htm 並選取 HTML 檢視。  將下列各行加入至 HTML 程式碼。  應該在 `</OBJECT>` 之後，但在 `</BODY>` 之前加入它們。  
  
    ```  
  
    <SCRIPT LANGUAGE="VBScript">  
    <!--  
    Sub PolyCtl_ClickIn(x, y)  
       PolyCtl.Sides = PolyCtl.Sides + 1  
    End Sub  
    Sub PolyCtl_ClickOut(x, y)  
       PolyCtl.Sides = PolyCtl.Sides - 1  
    End Sub  
    -->  
    </SCRIPT>  
    ```  
  
2.  儲存 HTM 檔案。  
  
 您已經加入一些 VBScript 程式碼，該程式碼從控制項取得 Sides 屬性，如果您按一下控制項內部則將邊數增加一。  如果您在控制項外部按一下，邊數就會減一。  
  
## 表示控制項可安全處理指令碼。  
 您可以用 Internet Explorer 的控制項檢視網頁，或更方便地，使用內建的 Visual C\+\+ Web 瀏覽器檢視。  若要在 Web 瀏覽器中檢視您的控制項，請以滑鼠右鍵按一下 PolyCtl.htm，然後按一下 \[**在瀏覽器中檢視**\]。  
  
 根據您目前的 Internet Explorer 安全性設定，您可能會收到安全性警示對話方塊，說明控制項可能不安全而且可能會造成損害。  例如，如果您有一個顯示檔案的控制項，也有刪除檔案的 `Delete` 方法，則僅在頁面上檢視該檔案較為安全。  這對指令碼來說並不安全，因為有人可以呼叫 `Delete` 方法。  
  
> [!IMPORTANT]
>  在本教學課程中，您可以變更 Internet Explorer 中的安全性設定，以執行未標示為安全的 ActiveX 控制項。  在控制台中，按一下 \[**網際網路屬性**\]，並按一下 \[**安全性**\] 以變更適當設定。  當您完成本教學課程時，將您的安全性設定變更回其原始狀態。  
  
 您可以用程式設計方式警示 Internet Explorer，不需要對這個特定控制項顯示 \[安全性警示\] 對話方塊。  您可以使用 `IObjectSafety` 介面完成這項作業，而且 ATL 在 [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md) 類別中提供這個介面的實作。  若要將介面加入至控制項，請將 `IObjectSafetyImpl` 加入至繼承的類別清單中，並在 COM 對應中加入它的項目。  
  
#### 若要將 IObjectSafetyImpl 加入至控制項  
  
1.  將下列行加入至 PolyCtl.h 中繼承類別清單的結尾，並且在上一行加入逗號：  
  
     [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]  
  
2.  將下列程式碼行加入至 PolyCtl.h 中的 .COM 對應：  
  
     [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/CPP/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]  
  
## 建置和測試控制項  
 建置控制項。  組建完成後，在瀏覽器檢視中重新開啟 PolyCtl.htm。  此時應該會直接顯示網頁，而不顯示 \[安全警告\] 對話方塊。  按一下多邊形內部，邊數會增加一。  按一下多邊形外部，邊數會減少一。  如果您嘗試將邊數減少到三個以下，將會看到您設定的錯誤訊息。  
  
 [回到步驟 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)  
  
## 後續步驟  
 這總結 ATL 教學課程。  如需 ATL 詳細資訊的連結，請參閱 [ATL 起始頁](../atl/active-template-library-atl-concepts.md)。  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)