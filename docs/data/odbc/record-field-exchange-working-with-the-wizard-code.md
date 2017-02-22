---
title: "資料錄欄位交換：精靈程式碼的使用 | Microsoft Docs"
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
  - "DoFieldExchange 方法, 覆寫"
  - "欄位資料成員"
  - "欄位資料成員, 宣告"
  - "m_nFields 資料成員"
  - "m_nFields 資料成員, 初始化"
  - "m_nParams 資料成員"
  - "m_nParams 資料成員, 初始化"
  - "ODBC, RFX"
  - "覆寫, DoFieldExchange"
  - "RFX (ODBC), 實作"
  - "RFX (ODBC), 精靈程式碼"
  - "Unicode, 和資料庫類別"
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 資料錄欄位交換：精靈程式碼的使用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明 \[MFC 應用程式精靈\] 和 \[加入類別\] \(如[加入 MFC ODBC 消費者](../../mfc/reference/adding-an-mfc-odbc-consumer.md)中所說明的\) 寫入支援 RFX 的程式碼，以及您要變更程式碼的方法。  
  
> [!NOTE]
>  這個主題適用於未實作大量資料列擷取的 `CRecordset` 衍生物件。  如果您要使用大量資料列擷取，就實作大量資料錄欄位交換 \(Bulk RFX\)。  Bulk RFX 類似 RFX。  若要了解兩者間的差異，請參閱[資料錄集：擷取 大量資料錄 \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)。  
  
 當您使用 \[MFC 應用程式精靈\] 或 \[加入類別\] 來建立資料錄集類別，精靈會根據資料來源、資料表和您在精靈中選取的資料行來為您撰寫下列之與 RFX 相關的項目：  
  
-   資料錄集類別內之資料錄集欄位資料成員的宣告。  
  
-   `CRecordset::DoFieldExchange` 的覆寫函式。  
  
-   資料錄集類別建構函式裡的資料錄集欄位資料成員的初始化。  
  
##  <a name="_core_the_field_data_member_declarations"></a> 欄位資料成員宣告  
 精靈會在 .h 檔內寫入資料錄集類別的宣告，類似下列 `CSections` 類別的宣告：  
  
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
  
 如果您要加入您自己繫結的參數資料成員或新的欄位資料成員，請在精靈先產生一個後再將其加入。  
  
 此外，請注意精靈會覆寫 `CRecordset` 類別的 `DoFieldExchange` 成員函式。  
  
##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange 覆寫函式  
 [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) 是 RFX 的主要部分。  架構會在任何需要於資料來源和資料錄集間移動資料的時候，呼叫 `DoFieldExchange`。  `DoFieldExchange` 也支援透過 [IsFieldDirty](../Topic/CRecordset::IsFieldDirty.md) 和 [IsFieldNull](../Topic/CRecordset::IsFieldNull.md) 成員函式，來取得欄位資料成員的資訊。  
  
 下列是 `CSections` 類別的 `DoFieldExchange` 覆寫函式。  精靈會為您的資料錄集類別將此函式寫入 .cpp 檔。  
  
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
  
 請注意以下的此函式主要功能：  
  
-   這個部分的函式稱為欄位對應。  
  
-   透過 `pFX` 指標呼叫 `CFieldExchange::SetFieldType`。  這個呼叫會指定 RFX 函式呼叫到 `DoFieldExchange` 的結尾，或對 `SetFieldType` 的下一個呼叫是輸出資料行。  如需詳細資訊，請參閱 [CFieldExchange::SetFieldType](../Topic/CFieldExchange::SetFieldType.md)。  
  
-   幾個 `RFX_Text` 全域函式的呼叫；每個欄位資料成員一個 \(範例中的全都是 `CString` 變數\)。  這些呼叫指定資料來源上的資料行名稱和欄位資料成員間的關聯性。  RFX 函式會實際的資料傳輸。  類別庫為所有通用資料型別提供 RFX 函式。  如需有關 RFX 函式的詳細資訊，請參閱[資料錄欄位交換：RFX 函式的使用](../../data/odbc/record-field-exchange-using-the-rfx-functions.md)。  
  
    > [!NOTE]
    >  在您的結果集 \(Result Set\) 內的資料行順序，必須與在 `DoFieldExchange` 內 RFX 函式呼叫順序相符。  
  
-   當架構呼叫 `DoFieldExchange` 時，`pFX` 指標會指向架構傳遞的 [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) 物件。  `CFieldExchange` 物件指定 `DoFieldExchange` 要執行的作業、傳輸方向和其他內容資訊。  
  
##  <a name="_core_the_recordset_constructor"></a> 資料錄集建構函式  
 精靈寫入的資料錄集建構函式包含兩件與 RFX 相關的事：  
  
-   每個欄位資料成員的初始化。  
  
-   包含欄位資料成員數目的 [m\_nFields](../Topic/CRecordset::m_nFields.md) 資料成員的初始化。  
  
 `CSections` 資料錄集的建構函式範例看起像是：  
  
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
>  如果您手動加入欄位資料成員，且您可以動態的繫結新增的資料行，就必須遞增 `m_nFields`。  您可以附加其他的程式碼行來達成，諸如：  
  
```  
m_nFields += 3;  
```  
  
 這是一個加入三個新增的欄位時之程式碼。  如果您加入了任何的參數資料成員，就必須初始化包含參數資料成員數目的 [m\_nParams](../Topic/CRecordset::m_nParams.md) 資料成員。  在方括弧外放置 `m_nParams` 初始化。  
  
## 請參閱  
 [資料錄欄位交換 \(RFX\)](../../data/odbc/record-field-exchange-rfx.md)