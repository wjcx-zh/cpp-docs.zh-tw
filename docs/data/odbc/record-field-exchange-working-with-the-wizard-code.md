---
title: 資料錄欄位交換： 精靈程式碼的使用 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d4f817ebfc3e6bb72865b4fc71fd5c5ebe5f671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>資料錄欄位交換：精靈程式碼的使用
本主題說明的程式碼，MFC 應用程式精靈和**加入類別**(中所述[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) 以支援 RFX 和您可能要變更程式碼的方式撰寫。  
  
> [!NOTE]
>  本主題適用於衍生自類別`CRecordset`的大量資料列中擷取尚未實作。 如果您使用大量資料列擷取，被實作大量資料錄欄位交換 (Bulk RFX)。 大量 RFX 與 RFX 相似。 若要了解的差異，請參閱[資料錄集： 擷取記錄中大量 (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 當您使用 MFC 應用程式精靈建立資料錄集類別或**加入類別**，精靈會根據資料來源資料表，而且您在精靈中進行選取的資料行，撰寫下列 RFX 相關的項目：  
  
-   資料錄集類別中的資料錄集欄位資料成員的宣告  
  
-   覆寫 `CRecordset::DoFieldExchange`  
  
-   初始化資料錄集類別建構函式中的資料錄集欄位資料成員  
  
##  <a name="_core_the_field_data_member_declarations"></a> 欄位資料成員宣告  
 精靈會如下所示，類別的.h 檔案中寫入資料錄集類別宣告`CSections`:  
  
```  
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
  
 如果您新增的參數資料成員或您自己繫結的新欄位資料成員，請將其加入的精靈產生的項目之後。  
  
 此外，請注意，精靈會覆寫`DoFieldExchange`類別成員函式`CRecordset`。  
  
##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 覆寫  

 [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) RFX 核心。 這個架構會呼叫`DoFieldExchange`次需要將資料從資料錄集的資料來源或從資料錄集移至資料來源。 `DoFieldExchange` 也支援取得有關的資訊欄位資料成員透過[IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty)和[IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull)成員函式。  
  
 下列`DoFieldExchange`覆寫為`CSections`類別。 精靈會撰寫資料錄集類別的.cpp 檔案中的函式。  
  
```  
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
  
 請注意下列重要功能的函式：  
  
-   本章節的函式會呼叫欄位對應。  
  
-   呼叫`CFieldExchange::SetFieldType`，到`pFX`指標。 此呼叫會指定所有 RFX 函式都呼叫的結尾`DoFieldExchange`或到下一個呼叫`SetFieldType`輸出資料行。 如需詳細資訊，請參閱[CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype)。  
  
-   數個呼叫`RFX_Text`全域函式，其中每個欄位資料成員 (所有可`CString`在範例中的變數)。 這些呼叫會指定資料來源上的資料行名稱和欄位資料成員之間的關聯性。 RFX 函式會執行實際的資料傳輸。 類別庫提供 RFX 函式之所有常見的資料類型。 如需 RFX 函式的詳細資訊，請參閱[資料錄欄位交換： RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。  
  
    > [!NOTE]
    >  在結果集資料行的順序必須符合 RFX 函式呼叫中的順序`DoFieldExchange`。  
  
-   `pFX`指標[CFieldExchange](../../mfc/reference/cfieldexchange-class.md)架構傳遞時，它會呼叫物件的`DoFieldExchange`。 `CFieldExchange`物件指定的作業，`DoFieldExchange`是執行，轉移，以及其他內容資訊的方向。  
  
##  <a name="_core_the_recordset_constructor"></a> 資料錄集建構函式  
 資料錄集建構函式精靈寫入包含與 RFX 兩件事：  
  
-   每個欄位資料成員初始設定  
  
-   初始化[m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)資料成員，其中包含的欄位資料成員的數目  
  
 建構函式`CSections`資料錄集範例看起來像這樣：  
  
```  
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
>  如果您加入欄位資料成員以手動方式，您可以動態地繫結新的資料行，您必須遞增`m_nFields`。 執行此作業藉由附加另一行程式碼，例如：  
  
```  
m_nFields += 3;  
```  

 這是程式碼以新增三個新的欄位。 如果您新增任何參數的資料成員時，您必須初始化[m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)資料成員，其中包含參數資料成員的數目。 Put`m_nParams`外方括號初始化。  

  
## <a name="see-also"></a>另請參閱  
 [資料錄欄位交換 (RFX)](../../data/odbc/record-field-exchange-rfx.md)