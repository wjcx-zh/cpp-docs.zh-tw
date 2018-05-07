---
title: 資料錄集： 架構 (ODBC) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5be3ec16ec01a6c6db2e24b1b6a6260f3a44bfec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-architecture-odbc"></a>資料錄集：架構 (ODBC)
本主題適用於 MFC ODBC 類別。  
  
 本主題說明組成的資料錄集物件架構的資料成員：  
  
-   [欄位資料成員](#_core_field_data_members)  
  
-   [參數資料成員](#_core_parameter_data_members)  
  
-   [使用 m_nFields 和 m_nParams 資料成員](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  本主題適用於衍生自物件`CRecordset`的大量資料列中擷取尚未實作。 如果實作大量資料列擷取時，架構就會是類似。 若要了解的差異，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_a_sample_class"></a> 範例類別  
 當您使用[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)從**加入類別**精靈，以宣告的資料錄集類別衍生自`CRecordset`，產生的類別已顯示在下列簡單的一般結構類別：  
  
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
  
 開頭的類別時，精靈會寫入一組[欄位資料成員](#_core_field_data_members)。 當您建立類別時，您必須指定一個或多個欄位資料成員。 如果類別參數化，與範例類別是 (與資料成員`m_strIDParam`)，您必須手動加入[參數資料成員](#_core_parameter_data_members)。 精靈不支援將參數加入至類別。  
  
##  <a name="_core_field_data_members"></a> 欄位資料成員  
 最重要的資料錄集類別成員是欄位資料成員。 針對您選取資料來源的每個資料行，此類別會包含該資料行的適當資料類型的資料成員。 例如，[範例類別](#_core_a_sample_class)這個開頭顯示主題有兩個欄位資料成員，這兩個型別`CString`，稱為`m_strCourseID`和`m_strCourseTitle`。  
  
 當資料錄集選取一組記錄時，架構會自動將繫結目前記錄的資料行 (之後**開啟**呼叫，目前是第一筆記錄) 物件的欄位資料成員。 也就是說，架構會使用適當的欄位資料成員做為緩衝區，以用來儲存記錄資料行的內容。  
  
 當使用者捲動至新的記錄，架構會使用欄位資料成員來代表目前的記錄。 架構會重新整理欄位資料成員，以取代前一筆記錄的值。 更新目前的記錄，以及加入新的記錄，也會使用欄位資料成員。 更新一筆記錄的程序的一部分，您可以將值指派給適當的欄位資料成員或成員，直接指定了更新的值。  
  
##  <a name="_core_parameter_data_members"></a> 參數資料成員  
 如果類別參數化，它會有一或多個參數的資料成員。 參數化的類別可讓您取得，或在執行階段計算資訊的基礎資料錄集查詢。  
  
 一般而言，此參數可協助縮小選取範圍，如下列範例所示。 根據[範例類別](#_core_a_sample_class)本主題開頭的資料錄集物件可能會執行下列 SQL 陳述式：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
 「？ 」 是您在執行階段提供參數值的預留位置。 當您建構資料錄集，並設定其`m_strIDParam`MATH101 資料成員，會變成資料錄集的有效 SQL 陳述式：  
  
```  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
 藉由定義的參數資料成員，您可以告知架構 SQL 字串中之參數。 架構會繫結的參數，可讓 ODBC 知道如何取得值，以取代的預留位置。 在範例中，產生的資料錄集包含只具有 CourseID 資料行，其值是 MATH101 Course 資料表中的記錄。 選取這筆記錄的所有指定的資料行。 您可以指定多個參數 （和預留位置） 視需要。  
  
> [!NOTE]
>  MFC 就不會執行任何動作本身使用的參數，特別是，不會執行文字替換。 相反地，MFC 會告知 ODBC 何處取得參數;ODBC 擷取資料，並且執行必要的參數化。  
  
> [!NOTE]
>  參數的順序很重要。 如需詳細資訊和參數的詳細資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams  

 當精靈寫入您的類別的建構函式時，它也會初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)指定數目的資料成員[欄位資料成員](#_core_field_data_members)類別中。 如果您新增任何[參數](#_core_parameter_data_members)至類別，您也必須新增個別的初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)資料成員，指定參數資料成員的數目。 架構會使用這些值與資料成員。  
  
 如需詳細資訊和範例，請參閱[資料錄欄位交換： RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)   
 [資料錄集： 宣告資料表 (ODBC) 的類別](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)   
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)