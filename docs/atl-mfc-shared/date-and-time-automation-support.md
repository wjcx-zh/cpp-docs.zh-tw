---
title: "Date and Time: Automation Support | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adding dates"
  - "Automation, date and time support"
  - "calculating dates and times"
  - "計算, 日期和時間"
  - "COleDateTime class, Automation date/time support"
  - "COleDateTimeSpan class, Automation date/time support"
  - "日期, Automation support"
  - "已耗用時間, calculating in Automation"
  - "格式化 [Visual Studio], 日期"
  - "格式化 [Visual Studio], 時間"
  - "時間 [Visual Studio], Automation support"
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time: Automation Support
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文件說明如何使用類別庫服務相關的日期和時間排列。  所描述的程序如下:  
  
-   [取得目前的時間](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [計算已耗用時間。](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [格式化日期\/時間字串表示。](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 類別提供表示日期和時間資訊。  它會 [CTime](../atl-mfc-shared/reference/ctime-class.md) 類別的更細微性和更進一步的範圍。  [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 類別表示已耗用時間，例如 `COleDateTime` 兩個物件之間的差異。  
  
 `COleDateTime` 和 `COleDateTimeSpan` 類別是設計來搭配用來自動化的 `COleVariant` 類別。  `COleDateTime` 和 `COleDateTimeSpan` 也適用於 MFC 程式設計的資料庫，不過，可以使用它們，每當您要管理的日期和時間值。  雖然 `COleDateTime` 類別來 `CTime` 類別具有值和更細微的更大的範圍，則會 `CTime`需要更多儲存每一個物件。  在與基礎 **DATE** 型別時，也有一些特殊考量。  如需的詳細資訊請參閱 [Date 型別](../atl-mfc-shared/date-type.md) 在 **DATE**的實作。  
  
 `COleDateTime` 物件可以用來表示在 31 年 1 月 1 日，介於 100 與 9999 之間的日期，十二月。  `COleDateTime` 物件是浮點數值，具有 1 毫秒的近似解析。  `COleDateTime` 根據 **DATE** 資料型別，定義在 [COleDateTime::operator 日期](../Topic/COleDateTime::operator%20DATE.md)下的 MFC 文件。  **DATE** 的實際實作在這些界限以外。  `COleDateTime` 實作施加這些繫結可以簡化與類別一起使用。  
  
 不支援`COleDateTime` 凱撒曆日期。  西曆假設 Just\-In\-Time 擴充為 Jan 100， 1。  
  
 `COleDateTime` 忽略日光節約時間 \(DST\)。  下列程式碼範例會比較計算交叉 DST 大進行變更的日期時間兩個方法:一個使用 CRT 和其他使用 `COleDateTime`。  DST 參數，在大部分的地區設定，第二個星期、和在 10 月第三個的。  
  
 使用標準 C 類型結構 **tm** 和 `time_t`，第一個方法分別設定兩 `CTime` 物件， *time1* 和 *time2*，對 4 月 5 日和 4 月 6 日。  程式碼會顯示 *time1* 和 *time2* 和時間這兩者。  
  
 第二個方法會建立兩個物件 `COleDateTime` 、 `oletime1` 和 `oletime2`，並設定為日期和 *time1* 和 *time2*相同。  它會顯示 `oletime1` 和 `oletime2` 和時間這兩者。  
  
 CRT 正確計算 23 小時差異。  `COleDateTimeSpan` 計算 24 小時差異。  
  
 請注意，使用 `COleDateTime::Format`作業在這個範例的結尾附近用來正確顯示日期。  請參閱知識庫文章\<BUG:%D 格式 \(「」\)。 `COleDateTime` 和 `COleDateTimeSpan`為」\(Q167338\)。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/CPP/date-and-time-automation-support_1.cpp)]  
  
## 請參閱  
 [Date and Time](../atl-mfc-shared/date-and-time.md)