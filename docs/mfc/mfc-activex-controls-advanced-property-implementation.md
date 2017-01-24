---
title: "MFC ActiveX 控制項：進階屬性實作 | Microsoft Docs"
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
  - "MFC ActiveX 控制項, 錯誤碼"
  - "MFC ActiveX 控制項, 屬性"
  - "屬性 [MFC], ActiveX 控制項"
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：進階屬性實作
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文將 ActiveX 控制項說明主題與實作進階屬性相關:  
  
-   [唯讀和唯寫屬性](#_core_read2donly_and_write2donly_properties)  
  
-   [傳回屬性中的錯誤碼](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a> 唯讀和唯寫屬性  
 加入屬性精靈會提供快速而輕鬆的方式實作控制項的唯讀或唯寫屬性。  
  
#### 實作唯讀或唯寫屬性  
  
1.  載入控制項的專案。  
  
2.  在類別檢視中，展開您的控制項程式庫節點。  
  
3.  以滑鼠右鍵按一下控制項的 \(程式庫節點的第二個節點介面節點\) 開啟捷徑功能表。  
  
4.  從捷徑功能表上，按一下 **Add** 然後按一下 \[**加入屬性**\]。  
  
     這樣會開啟 [加入屬性精靈](../ide/names-add-property-wizard.md)。  
  
5.  在 **Property Name** 方塊中，輸入您的屬性名稱。  
  
6.  對於 **Implementation Type**，按一下 **Get\/Set Methods**。  
  
7.  在 **Property Type** 方塊中，為屬性選取適當的型別。  
  
8.  如果您想要唯讀屬性，清除集合函式名稱。  如果您想要唯寫屬性，請清除 Get 函式名稱。  
  
9. 按一下 \[**完成**\]。  
  
 這樣做時，加入屬性精靈會在分派對應項目插入函式 `SetNotSupported` 或 `GetNotSupported` 在一般集合或 Get 函式位置。  
  
 若要變更現有的屬性是唯讀或唯寫，您可以手動編輯分派對應和從控制項移除不必要的設定或取得函式。  
  
 如果您希望屬性條件式唯讀或唯寫的 \(例如，在中，只有在您的控制項處於特定模式下操作\)，在適當時您可以設定或取得函式，一般，並呼叫 `SetNotSupported` 或 `GetNotSupported` 函式。  例如：  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/CPP/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 如果 `m_bReadOnlyMode` 資料成員是 **TRUE**，這個程式碼範例會呼叫 `SetNotSupported` 。  如果 **FALSE**，屬性就會設定為新值。  
  
##  <a name="_core_returning_error_codes_from_a_property"></a> 傳回屬性中的錯誤碼  
 表示發生錯誤時，會嘗試取得或設定屬性，請使用 `COleControl::ThrowError` 函式，採用 `SCODE` \(狀態碼\) 做為參數。  您可以使用預先定義的 `SCODE` 或定義人員你。  如需預先定義 `SCODE`所定義的自訂 `SCODE`清單和指示，請參閱下列文章 ActiveX 控制項的 [在您的 ActiveX 控制項的處理錯誤](../mfc/mfc-activex-controls-advanced-topics.md) :進階主題。  
  
 Helper 函式為最常用的預先定義 `SCODE`存在，例如 [COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)、 [COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)和 [COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)。  
  
> [!NOTE]
>  `ThrowError` 被視為只用來做為傳回錯誤的方法是從屬性取得的內部或 Set 函式或自動化方法。  這些是唯一的紀元適當的例外處理常式會出現在堆疊。  
  
 如需程式碼的其他區域的報告例外狀況的詳細資訊，請參閱 [COleControl::FireError](../Topic/COleControl::FireError.md) 和區段在文件 ActiveX 控制項的 [在您的 ActiveX 控制項的處理錯誤](../mfc/mfc-activex-controls-advanced-topics.md) :進階主題。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控制項：屬性](../mfc/mfc-activex-controls-properties.md)   
 [MFC ActiveX 控制項：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)