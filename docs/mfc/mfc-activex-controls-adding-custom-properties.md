---
title: "MFC ActiveX 控制項：加入自訂屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ActiveX 控制項, 屬性"
  - "屬性 [MFC], 自訂"
ms.assetid: 85af5167-74c7-427b-b8f3-e0d7b73942e5
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：加入自訂屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自訂屬性與內建屬性不同的自訂屬性不為 `COleControl` 類別已經實作。  自訂屬性來公開 ActiveX 控制項的某些狀態或外觀。使用控制項的程式設計人員。  
  
 本文說明如何將自訂屬性加入至 ActiveX 控制項加入屬性精靈並說明產生的程式碼修改。  主題包括：  
  
-   [使用將加入屬性精靈的自訂屬性。](#_core_using_classwizard_to_add_a_custom_property)  
  
-   [加入屬性的自訂精靈變更](#_core_classwizard_changes_for_custom_properties)  
  
 自訂屬性的方式來實作四種:成員變數，以通知， Get\/Set 方法的成員變數和參數化。  
  
-   成員變數實作  
  
     這個實作所表示屬性的狀態為控制項類別的 10% 成員變數。  請使用成員變數實作，當知道不重要的屬性值變更時。  三個型別，這個實作會建立屬性的最少量的支援程式碼。  成員變數實作的分派對應項巨集是 [DISP\_PROPERTY](../Topic/DISP_PROPERTY.md)。  
  
-   與通知實作的成員變數  
  
     這個實作中加入屬性精靈和告知函式所建立的成員變數。  在屬性值變更後，告知函式由架構會自動呼叫。  請使用與通知實作的成員變數，並在需要時收到通知，在屬性值變更之後。  因為它需要函式呼叫，這個實作需要更多時間。  這個實作的分派對應項巨集是 [DISP\_PROPERTY\_NOTIFY](../Topic/DISP_PROPERTY_NOTIFY.md)。  
  
-   取得\/設定方法實作  
  
     這個實作包含一個控制項類別的成員函式。  取得\/設定方法實作會呼叫取得成員函式，當控制項的使用者要求屬性的目前值和成員函式時，變更屬性的控制項的使用者要求時。  請使用這個實作會在執行階段期間，也就是說，當您需要計算屬性值時，驗證控制項傳遞的值在變更實際屬性之前或實作讀取或唯寫屬性型別。  這個實作的分派對應項巨集是 [DISP\_PROPERTY\_EX](../Topic/DISP_PROPERTY_EX.md)。  下列章節， [使用將加入屬性精靈的自訂屬性](#_core_using_classwizard_to_add_a_custom_property)，使用 CircleOffset 自訂屬性示範這項實作。  
  
-   參數化的實作  
  
     參數型實作會加入屬性精靈支援。  參數化屬性 \(有時稱為屬性陣列\) 可以用來將控制單一屬性存取一組值。  這個實作的分派對應項巨集是 `DISP_PROPERTY_PARAM`。  如需實作型別的詳細資訊，請參閱下列文章 ActiveX 控制項的 [實作參數化屬性](../mfc/mfc-activex-controls-advanced-topics.md) :進階主題。  
  
##  <a name="_core_using_classwizard_to_add_a_custom_property"></a> 使用將加入屬性精靈的自訂屬性。  
 下列程序示範如何將自訂屬性， CircleOffset，使用 Get\/Set 方法實作。  CircleOffset 自訂屬性可讓控制項的使用者控制項位移的周框矩形的中心的圓形。  加入的自訂屬性與方法除了 Get\/Set 方法以外的實作很相似。  
  
 這個程序也可以用來加入您想要的其他自訂屬性。  用 CircleOffset 屬性名稱和參數替代自訂屬性名稱。  
  
#### 使用加入屬性精靈，將 CircleOffset 自訂屬性  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
     這樣會開啟 [加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在 \[**屬性名稱**\] 方塊中輸入 `CircleOffset`。  
  
6.  對於 **Implementation Type**，按一下 **Get\/Set Methods**。  
  
7.  在 **Property Type** 方塊中，選取 **short**。  
  
8.  輸入唯一名稱您的 Get 和 Set 函式或接受預設名稱。  
  
9. 按一下 \[**完成**\]。  
  
##  <a name="_core_classwizard_changes_for_custom_properties"></a> 加入屬性的自訂精靈變更  
 當您將 CircleOffset 自訂屬性時，加入屬性精靈會對標題 \(。H\) 和控制項的實作 \(.CPP\) 檔案分類。  
  
 下列程式碼行加入至。宣告兩個函式的 H 檔案呼叫 `GetCircleOffset` 和 `SetCircleOffset`:  
  
 [!code-cpp[NVC_MFC_AxUI#25](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_1.h)]  
  
 下列程式碼行加入至控制項的.IDL 檔案:  
  
 [!code-cpp[NVC_MFC_AxUI#26](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_2.idl)]  
  
 這一行會將 CircleOffset 屬性每個特定 ID 編號，並以加入屬性精靈方法和屬性清單中方法的位置。  
  
 此外，下列程式行加入至分派對應 \(控制項類別的 .CPP 檔案\) 對應 CircleOffset 屬性加入至控制項的兩個處理常式函式:  
  
 [!code-cpp[NVC_MFC_AxUI#27](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_3.cpp)]  
  
 最後， `GetCircleOffset` 的實作和 `SetCircleOffset` 函式加入至控制項的 .CPP 檔案結尾。  在大部分情況下，您將修改 Get 函式傳回屬性的值。  這個 Set 函式通常會包含應該實作或的程式碼，在屬性變更前後。  
  
 [!code-cpp[NVC_MFC_AxUI#28](../mfc/codesnippet/CPP/mfc-activex-controls-adding-custom-properties_4.cpp)]  
  
 請注意加入屬性精靈會自動將呼叫，加入至 [SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md)，為 Set 函式的主體。  呼叫此函式將控制項標記為已修改。  如果修改了控制項，則新的控制項狀態儲存，當容器中。  應該呼叫這個函式，當屬性，儲存為控制項的持續性狀態中，變更值。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)