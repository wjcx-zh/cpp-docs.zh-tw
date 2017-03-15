---
title: "資料錄集：架構 (ODBC) | Microsoft Docs"
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
  - "欄位資料成員"
  - "欄位資料成員, 資料錄集架構"
  - "m_nFields 資料成員"
  - "m_nFields 資料成員, 資料錄集"
  - "m_nParams 資料成員"
  - "m_nParams 資料成員, 資料錄集"
  - "ODBC 資料錄集, 架構"
  - "資料錄集中的參數資料成員"
  - "資料錄集, 架構"
  - "資料錄集, 資料成員"
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄集：架構 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本文件適用於 MFC ODBC 類別。  
  
 這個主題說明構成資料錄集物件架構的資料成員：  
  
-   [欄位資料成員](#_core_field_data_members)  
  
-   [參數資料成員](#_core_parameter_data_members)  
  
-   [使用 m\_nFields 和 m\_nParams 資料成員](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  本文件適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  此種架構在實作大量資料列擷取時仍是類似的。  若要了解兩者間的差異，請參閱[資料錄集：擷取 大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_a_sample_class"></a> 範例類別  
 當您使用 **Add Class** 精靈的 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)，來宣告衍生自 `CRecordset` 的資料錄集類別時，產生的類別會具有如下列範例類別所示的一般結構：  
  
```  
class CCourse : public CRecordset  
{  
public:  
   CCourse(CDatabase* pDatabase = NULL);  
   ...  
   CString m_strCourseID;  
   CString m_strCourseTitle;  
   CString m_strIDParam;  
};  
```  
  
 精靈會在類別開頭寫入一組[欄位資料成員](#_core_field_data_members)。  在您建立類別時，您必須指定一個或多個欄位資料成員。  如果該類別和範例類別一樣是參數化的 \(使用 `m_strIDParam` 資料成員\)，您就必須手動加入[參數資料成員](#_core_parameter_data_members)。  精靈並不支援將參數加入至類別中。  
  
##  <a name="_core_field_data_members"></a> 欄位資料成員  
 欄位資料成員是您的資料錄集類別中最重要的成員。  針對每個您選自資料來源的資料行，類別都會包含適用於該資料行資料型別的資料成員。  例如，在本主題開頭所示範的[範例類別](#_core_a_sample_class)，擁有名為 `m_strCourseID` 和 `m_strCourseTitle` 的兩個欄位資料成員，兩者都是 `CString` 型別。  
  
 當資料錄集選取一組資料錄時，架構 \(Framework\) 會自動將目前資料錄 \(在 **Open** 呼叫後的第一個資料錄即是目前的\) 的資料行繫結至物件的欄位資料成員。  也就是說架構會將合適的欄位資料成員當做緩衝區，以便儲存資料錄資料行內容。  
  
 當使用者捲動至一筆新資料錄時，架構會使用欄位資料成員來表示目前的資料錄。  架構會重新整理欄位資料成員，以便取代之前的資料錄值。  欄位資料成員亦可用於目前資料錄的更新或新資料錄的加入。  您可以在更新一筆資料錄的過程中，在合適的欄位資料成員或成員中直接設定值便可指定更新值。  
  
##  <a name="_core_parameter_data_members"></a> 參數資料成員  
 類別如果已經參數化處理，便會擁有一個或多個參數資料成員。  一個參數型類別讓您可根據在執行階段中所取得或計算出來的資訊建立一個資料錄集查詢。  
  
 一般說來，參數有助於縮小選取範圍，請參閱下示範例。  根據這個主題開頭所提及的[範例類別](#_core_a_sample_class)，資料錄集物件可能會執行下列 SQL 陳述式：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 "?" 是一個您在執行階段提供的參數值之替代符號 \(Placeholder\)。  當您建構資料錄集並將資料錄集的 `m_strIDParam` 資料成員設定為 MATH101 時，資料錄集的有效 SQL 陳述式就會成為：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 您可藉由定義參數資料成員，告知架構在 SQL 字串 \(String\) 中的參數為何。  架構會繫結該參數，讓 ODBC 清楚該取何處的值來置換替代符號。  範例中所產生的資料錄集僅包含在 Course 資料表的 CourseID 資料行中值為 MATH101 的資料錄。  這筆資料錄的指定資料行都已選取。  您可視需要來指定任意個參數 \(和替代符號\)。  
  
> [!NOTE]
>  MFC 本身對於參數沒有作用，而且不會執行文字替換。  相反地，MFC 會告知 ODBC 該至何處取得參數；ODBC 會擷取該筆資料並執行必要的參數化。  
  
> [!NOTE]
>  參數的順序是很重要的。  如需此動作和參數的詳細資訊，請參閱[資料錄集：參數化資料錄集 \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m\_nFields 和 m\_nParams  
 精靈在為類別寫入建構函式 \(Constructor\) 時，也會初始化 [m\_nFields](../Topic/CRecordset::m_nFields.md) 資料成員，此成員會指定在類別中的[欄位資料成員](#_core_field_data_members)數目。  若在類別中加入任何[參數](#_core_parameter_data_members)，則您也必須為 [m\_nParams](../Topic/CRecordset::m_nParams.md) 資料成員加入初始化，此成員會指定參數資料成員的數目。  架構會運用這些值來使用資料成員。  
  
 ‎如需範例和詳細資訊，請參閱[資料錄欄位交換：RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
## 請參閱  
 [資料錄集 \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [資料錄集：宣告資料表的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)