---
title: 資料錄欄位交換：精靈程式碼的使用
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 8e42fc9da672ca4ef97e775776935650ab7f545a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367120"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>資料錄欄位交換：精靈程式碼的使用

> [!NOTE]
> Visual Studio 2019 和更新版本中未提供「MFC ODBC 消費者」精靈。 您仍然可以手動建立消費者。

本主題說明「MFC 應用程式精靈」和 [新增類別]**** (如[新增 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所述) 所撰寫來支援 RFX 的程式碼，以及如何更改該程式碼。

> [!NOTE]
> 本主題適用於衍生自尚未實作大量資料列擷取之 `CRecordset` 的類別。 如果您使用大量資料列擷取，就會實作大量記錄欄位交換 (大量 RFX)。 大量 RFX 與 RFX 類似。 要瞭解差異,請參閱[記錄集:批量提取記錄 (ODBC)。](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

當您使用「MFC 應用程式精靈」或 [新增類別]**** 來建立資料錄集類別時，精靈會根據您在精靈中選擇的資料來源、資料表及資料行，為您撰寫下列 RFX 相關元素：

- 資料錄集類別中資料錄集欄位資料成員的宣告

- `CRecordset::DoFieldExchange` 的覆寫

- 資料錄集類別建構函式中資料錄集欄位資料成員的初始化

## <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a> 欄位資料成員宣告

精靈會在 .h 檔案中撰寫資料錄集類別宣告，類似以下 `CSections`類別的宣告：

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

如果您要新增自行繫結的參數資料成員或新欄位資料成員，請在精靈產生的資料成員後面新增它們。

此外，請注意精靈會覆寫 `CRecordset` 類別的 `DoFieldExchange` 成員函式。

## <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 覆寫

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) 是 RFX 的核心。 架構在每當需要將資料從資料來源移至資料錄集，或從資料錄集移至資料來源時，都會呼叫 `DoFieldExchange`。 `DoFieldExchange` 也支援透過 [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) 和 [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) 成員函式取得欄位資料成員的相關資訊。

下列 `DoFieldExchange` 覆寫適用於 `CSections` 類別。 精靈會在 .cpp 檔案中撰寫您資料錄集類別的函式。

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

請注意函式的下列重要功能：

- 函式的這個區段稱為欄位對應。

- 透過 `pFX` 指標對 `CFieldExchange::SetFieldType` 的呼叫。 這個呼叫會指定到 `DoFieldExchange` 結尾為止的所有 RFX 函式呼叫或下一個 `SetFieldType` 呼叫為輸出資料行。 如需詳細資訊，請參閱 [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。

- 數個 `RFX_Text` 全域函式呼叫 — 每一欄位資料成員一個呼叫 (在範例中全都是 `CString` 變數)。 這些呼叫會指定資料來源上的資料行名稱與欄位資料成員之間個關聯性。 RFX 函式會執行實際的資料傳輸。 類別程式庫支援所有常見資料類型的 RFX 函式。 有關 RFX 函數的詳細資訊,請參閱[記錄欄位交換:使用 RFX 函數](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。

    > [!NOTE]
    >  資料集內資料行的順序必須符合 `DoFieldExchange` 中 RFS 函式呼叫的順序。

- 架構在呼叫 `DoFieldExchange` 時所傳遞之 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 物件的 `pFX` 指標。 `CFieldExchange` 物件會指定設定 `DoFieldExchange` 來執行的作業、傳輸方向，以及其他內容資訊。

## <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a> 資料錄集建構函式

精靈所撰寫的資料錄集建構函式包含兩個與 RFX 相關的項目：

- 每個欄位資料成員的初始化

- 包含欄位資料成員數目之 [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) 資料成員的初始化

`CSections` 資料錄集範例的建構函式看起來像這樣：

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
> 如果您手動新增任何欄位資料成員 (如果您以動態方式繫結新資料行，就可能這麼做)，就必須讓 `m_nFields` 遞增。 若要這麼做，請附加另一行程式碼，例如：

```cpp
m_nFields += 3;
```

這是可新增三個新欄位的程式碼。 如果您新增任何參數資料成員，就必須將 [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) 資料成員初始化，此資料成員包含參數資料成員的數目。 請將 `m_nParams` 初始化放在括弧外。

## <a name="see-also"></a>另請參閱

[記錄現場交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)
