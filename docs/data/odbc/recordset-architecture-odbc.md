---
title: 資料錄集： 架構 (ODBC) |Microsoft Docs
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
ms.openlocfilehash: 0e45e16b42505d34ea4340b991638405e7161eb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030265"
---
# <a name="recordset-architecture-odbc"></a>資料錄集：架構 (ODBC)

本主題適用於 MFC ODBC 類別。  
  
本主題描述組成資料錄集物件架構的資料成員：  
  
- [欄位資料成員](#_core_field_data_members)  
  
- [參數資料成員](#_core_parameter_data_members)  
  
- [使用 m_nFields 和 m_nParams 資料成員](#_core_using_m_nfields_and_m_nparams)  
  
> [!NOTE]
>  本主題適用於物件衍生自`CRecordset`的大量資料列中擷取尚未實作。 如果實作大量資料列擷取時，架構會很類似。 若要了解這些差異，請參閱[資料錄集： 擷取記錄中大量資料庫連接 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
##  <a name="_core_a_sample_class"></a> 範例類別  

當您使用[MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)從**加入類別**精靈來宣告資料錄集類別衍生自`CRecordset`，產生的類別具有如下所示簡單的一般結構類別：  
  
```cpp  
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
  
類別的開頭時，精靈會將一組[欄位資料成員](#_core_field_data_members)。 當您建立類別時，您必須指定一或多個欄位資料成員。 如果類別參數化的範例類別是 (與資料成員`m_strIDParam`)，您必須手動新增[參數的資料成員](#_core_parameter_data_members)。 精靈不支援將參數加入至類別。  
  
##  <a name="_core_field_data_members"></a> 欄位資料成員  

最重要的資料錄集類別的成員是欄位資料成員。 針對您選取資料來源的每個資料行，此類別會包含該資料行的適當資料類型的資料成員。 例如，[範例類別](#_core_a_sample_class)這個開頭顯示主題有兩個欄位資料成員，這兩個型別`CString`，稱為`m_strCourseID`和`m_strCourseTitle`。  
  
當資料錄集選取一組記錄時，架構會自動繫結的目前資料錄的資料行 (之後`Open`呼叫時，第一筆記錄是最新) 至物件的欄位資料成員。 也就是架構會使用適當的欄位資料成員，作為用來儲存記錄資料行的內容緩衝區。  
  
當使用者捲動至新的記錄時，架構會使用代表目前資料錄的欄位資料成員。 架構會重新整理欄位資料成員，以取代前一筆記錄的值。 更新目前的記錄，以及加入新的記錄，也會使用欄位資料成員。 更新記錄的程序的一部分，您可以指定更新值直接將指派值給適當的欄位資料成員或成員。  
  
##  <a name="_core_parameter_data_members"></a> 參數資料成員  

如果類別已參數化，它會有一或多個參數的資料成員。 參數化的類別可讓您可根據資訊取得，或在執行階段計算的資料錄集的查詢。  
  
一般而言，參數有助於縮小選取範圍，如下列範例所示。 根據[範例類別](#_core_a_sample_class)本主題開頭的資料錄集物件可能會執行下列 SQL 陳述式：  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?  
```  
  
"？"是您在執行階段所提供的參數值的預留位置。 當您建構資料錄集並設定其`m_strIDParam`MATH101 資料成員，會成為有效的 SQL 陳述式資料錄集：  
  
```sql  
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101  
```  
  
藉由定義參數的資料成員，您告訴架構 SQL 字串中的參數。 架構會繫結的參數，可讓 ODBC 知道哪裡可以取得值，以取代預留位置。 在範例中，產生的資料錄集包含從具有 CourseID 資料行的值是 MATH101 Course 資料表的記錄。 選取這筆記錄的所有指定的資料行。 您可以指定任意數目的參數 （和預留位置） 如您所需要。  
  
> [!NOTE]
>  MFC 沒有本身使用的參數 — 特別是，不會執行文字替換。 相反地，MFC 會告訴 ODBC 何處取得參數;ODBC 擷取資料，並執行必要的參數化。  
  
> [!NOTE]
>  參數的順序很重要。 如需相關資訊和參數的詳細資訊，請參閱[資料錄集： 參數化資料錄集 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。  
  
##  <a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams  

當精靈將寫入您的類別的建構函式時，它也會初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)資料成員，指定的數目[欄位資料成員](#_core_field_data_members)類別中。 如果您新增任何[參數](#_core_parameter_data_members)至您的類別，您也必須新增個別的初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)資料成員，指定之參數的資料成員的數目。 架構會使用這些值使用的資料成員。  
  
如需詳細資訊和範例，請參閱 <<c0> [ 資料錄欄位交換： RFX 的使用](../../data/odbc/record-field-exchange-using-rfx.md)。  
  
## <a name="see-also"></a>另請參閱  

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)