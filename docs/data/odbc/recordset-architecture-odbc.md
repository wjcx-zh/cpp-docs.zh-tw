---
title: 資料錄集：架構 (ODBC)
ms.date: 11/04/2016
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
ms.openlocfilehash: e95250b5ef307eafdb334050fbace945355e0521
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079867"
---
# <a name="recordset-architecture-odbc"></a>資料錄集：架構 (ODBC)

本主題適用於 MFC ODBC 類別。

本主題描述構成資料錄集物件架構的資料成員：

- [欄位資料成員](#_core_field_data_members)

- [參數資料成員](#_core_parameter_data_members)

- [使用 m_nFields 和 m_nParams 資料成員](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的物件。 如果已實作大量資料列擷取，則架構會類似。 若要了解差異，請參閱[資料錄集：大量擷取記錄 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a> 範例類別

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供 MFC ODBC 消費者精靈。 您仍然可以手動建立消費者。

當您從 [新增類別] 精靈使用 [MFC ODBC 消費者精靈](../../mfc/reference/adding-an-mfc-odbc-consumer.md)來宣告衍生自 `CRecordset` 的資料錄集類別時，產生的類別會具有以下範例類別中所示的一般架構：

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

在此類別的開頭，精靈會撰寫一組[欄位資料成員](#_core_field_data_members)。 當您建立類別時，必須指定一或多個欄位資料成員。 如果此類別與範例類別 (含有資料成員 `m_strIDParam`) 一樣已參數化，您就必須手動新增[參數資料成員](#_core_parameter_data_members)。 精靈並不支援將參數新增至類別。

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a> 欄位資料成員

您資料錄集類別的最重要成員就是欄位資料成員。 針對您從資料來源選取的每個資料行，此類別會包含該資料行之適當資料類型的資料成員。 例如，本主題開頭顯示的[範例類別](#_core_a_sample_class)便有兩個欄位資料成員 (兩者的類型皆為 `CString`)，稱為 `m_strCourseID` 和 `m_strCourseTitle`。

當資料錄集選取一組記錄時，架構會自動將目前記錄的資料行 (在 `Open` 呼叫之後，第一個記錄是目前的記錄) 繫結至物件的欄位資料成員。 也就是說，架構會使用適當欄位資料成員作為可供儲存記錄資料行內容的緩衝區。

當使用者捲動至新記錄時，架構會使用欄位資料成員來代表目前的記錄。 架構會重新整理欄位資料成員，取代先前記錄的值。 欄位資料成員也會用來更新目前的記錄，以及新增新的記錄。 作為更新記錄程序的一部分，您需將值直接指派給適當的欄位資料成員，來指定更新值。

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a> 參數資料成員

如果類別已參數化，它就會有一或多個參數資料成員。 參數化類別可讓您的資料錄集查詢以在執行階段取得或計算出的資訊為基礎。

一般而言，參數有助於縮小選取範圍，如以下範例所示。 根據本主題開頭的[範例類別](#_core_a_sample_class)，資料錄集物件可以執行下列 SQL 陳述式：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" 是您在執行階段提供之參數值的預留位置。 當您建構資料錄集並將其 `m_strIDParam` 資料成員設定為 MATH101 時，資料錄集的有效 SQL 陳述式會變成：

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

藉由定義參數資料成員，您可以讓架構了解 SQL 字串中的參數。 架構會繫結參數，這可讓 ODBC 知道要去哪裡取得要替代預留位置的值。 在範例中，產生的資料錄集只會包含來自 Course 資料表且 CourseID 資料行值為 MATH101 的記錄。 系統會選取此記錄的所有指定資料行。 您可以依需求指定多個參數 (和預留位置)。

> [!NOTE]
>  MFC 本身不會對參數進行任何處理 — 特別是，不會執行文字替代。 取而代之的是，MFC 會告訴 ODBC 去哪裡取得參數；ODBC 會擷取資料並執行必要的參數化。

> [!NOTE]
>  參數的順序很重要。 如需有關參數的這項資訊及其他資訊，請參閱[資料錄集：將資料錄集參數化 (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)。

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a> 使用 m_nFields 和 m_nParams

當精靈為您的類別撰寫建構函式時，它也會將 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 資料成員初始化，以指定類別中[欄位資料成員](#_core_field_data_members)的數目。 如果您將任何[參數](#_core_parameter_data_members)新增至您的類別，則也必須為 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 資料成員新增初始化，以指定參數資料成員的數目。 架構會使用這些值來與資料成員搭配運作。

如需有關範例的詳細資訊，請參閱[記錄欄位交換：使用 RFX](../../data/odbc/record-field-exchange-using-rfx.md)。

## <a name="see-also"></a>另請參閱

[資料錄集 (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[資料錄集：宣告資料表的類別 (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)