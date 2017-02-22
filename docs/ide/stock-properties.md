---
title: "內建屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "內建屬性"
  - "內建屬性, 關於內建屬性"
ms.assetid: a89fc454-0b8e-447a-9033-4c8af46a24d9
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 內建屬性
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您正使用[加入屬性精靈](../ide/idl-attributes-add-property-wizard.md)，將屬性加入至 MFC 分配介面 \(Dispinterface\)，則可以從精靈中[名稱](../ide/names-add-property-wizard.md)頁面上的 \[**屬性名稱**\] 清單選取一個內建屬性。  這些屬性如下所示：  
  
|屬性名稱|描述|  
|----------|--------|  
|**外觀**|傳回或設定控制項外觀的值。  控制項的 **Appearance** 屬性可以包含或省略 3D 顯示效果。  這是一個環境讀\/寫屬性。|  
|`BackColor`|傳回控制項的環境 `BackColor` 屬性，或將其設定成調色盤 \(RGB\) 色彩或預先定義的系統色彩。  根據預設，它的值與控制項容器 \(Container\) 的前景色彩一致。  這是一個環境讀\/寫屬性。|  
|`BorderStyle`|傳回或設定控制項的框線樣式。  這是一個讀\/寫屬性。|  
|**Caption**|傳回或設定控制項的 **Caption** 屬性。  這個標題是視窗的標題。  **Caption** 並沒有**成員變數**實作類型。|  
|**Enabled**|傳回或設定控制項的 **Enabled** 屬性。  啟用控制項能夠對使用者所產生的事件做出回應。|  
|**Font**|傳回或設定控制項的環境字型。  如果控制項沒有字型，則為 Null。|  
|`ForeColor`|傳回或設定控制項的環境 `ForeColor` 屬性。|  
|**hWnd**|傳回或設定控制項的 **hWnd** 屬性。  **hWnd** 並沒有**成員變數**實作類型。|  
|**ReadyState**|傳回或設定控制項的 **ReadyState** 屬性。  控制項可以是未初始化、已初始化、正載入、互動式或完整的。  如需詳細資訊，請參閱《Internet SDK》中的 [READYSTATE](https://msdn.microsoft.com/en-us/library/aa768362.aspx)。|  
|**文字**|傳回或設定控制項內包含的文字。  **Text** 並沒有**成員變數**實作類型。|  
  
## 請參閱  
 [加入屬性](../ide/adding-a-property-visual-cpp.md)   
 [加入屬性精靈、IDL 屬性](../ide/idl-attributes-add-property-wizard.md)