---
title: "將屬性加入至控制項 (ATL 教學課程，第 3 部分) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
caps.latest.revision: 15
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將屬性加入至控制項 (ATL 教學課程，第 3 部分)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`IPolyCtl` 是包含控制項的自訂方法和屬性的介面，然後，您會將屬性加入至其中。  
  
### 使用加入屬性精靈，將屬性  
  
1.  在 \[類別檢視\] 中，展開多邊形分支。  
  
2.  以滑鼠右鍵按一下 IPolyCtl。  
  
3.  在捷徑功能表上，按一下 \[**新增**\]，然後按一下 \[**加入屬性**\]。  
  
     加入屬性精靈\] 隨即出現。  
  
4.  在屬性型別下拉式清單中，選取 `SHORT`。  
  
5.  輸入 `邊界` 做為 \[**屬性名稱。**\]  
  
6.  按一下  完成的 \[**完成**\] 加入屬性。  
  
 當您將屬性加入至 .idl 檔編譯\) 的介面， MIDL \(程式定義擷取其值的 `Get` 方法和設定新的值。 `Put` 方法。  方法會透過加上 `put_` 和 `get_` 命名的屬性名稱。  
  
 加入屬性精靈會將需要的程式碼行加入至 .idl 檔。  它也會將 `Get` 和 `Put` 函式原型加入至 PolyCtl.h 的類別定義並加入空白實作加入至 PolyCtl.cpp。  您可以開啟 PolyCtl.cpp 和搜尋函式則會檢查這個 `get_Sides` 和 `put_Sides`。  
  
 雖然您現在有擷取最基本的函式會設定和屬性，需要位置來儲存它。  您會建立變數以儲存屬性和據以更新函式。  
  
#### 建立變數以儲存屬性和更新放置和取得方法  
  
1.  從 \[方案總管\] 中，開啟 PolyCtl.h 和在 `m_clrFillColor`的定義之後加入下列程式碼:  
  
     [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]  
  
2.  設定預設值 `m_nSides`。  藉由加入行進行預設圖案三角形至 PolyCtl.h 的建構函式:  
  
     [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]  
  
3.  實作 `Get` 和 `Put` 方法。  `get_Sides` 和 `put_Sides` 函式宣告加入至 PolyCtl.h。  使用下列程式碼取代 PolyCtl.cpp `get_Sides` 的和 `put_Sides` 的程式碼:  
  
     [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/CPP/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]  
  
 `get_Sides` 方法傳遞 `pVal` 指標傳回 `Sides` 屬性目前的值。  在 `put_Sides` 方法中，程式碼會確保使用者設定 `Sides` 屬性設定為可接受值。  最少必須是介於 2 和，因為點陣列的每一邊將使用， 100 是最大值的合理的限制。  
  
 您現在有一個名為 `Sides`的屬性。  在下一個步驟中，您將變更繪圖程式碼使用。  
  
 [回到步驟 2](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [在 &#91;步驟 4](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)  
  
## 請參閱  
 [教學課程](../atl/active-template-library-atl-tutorial.md)