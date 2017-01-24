---
title: "SQL：自訂資料錄集的 SQL 陳述式 (ODBC) | Microsoft Docs"
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
  - "自訂 SQL 陳述式"
  - "ODBC 資料錄集, SQL 陳述式"
  - "覆寫, SQL 陳述式"
  - "資料錄集, SQL 陳述式"
  - "SQL 陳述式, 自訂"
  - "SQL 陳述式, 資料錄集"
  - "SQL, 開啟資料錄集"
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL：自訂資料錄集的 SQL 陳述式 (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個主題說明：  
  
-   此架構要如何建構 SQL 陳述式  
  
-   如何覆寫 SQL 陳述式  
  
> [!NOTE]
>  本資訊適用於 MFC ODBC 類別。  如果您正在使用 MFC DAO 類別，請參閱《DAO 說明》中的＜比較 Microsoft Jet Database Engine SQL 與 ANSI SQL＞主題。  
  
## SQL 陳述式建構  
 您的資料錄集主要是根據 SQL **SELECT** 陳述式建立資料錄選取。  當您使用精靈來宣告類別後，它會寫入 `GetDefaultSQL` 成員函式的覆寫版本，看來有些類似這個 \(稱為 `CAuthors` 的資料錄集類別\)。  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 預設情形是，這個覆寫函式會傳回您在精靈中所指定的資料表名稱。  範例中的資料表名稱是 "AUTHORS"。在您稍後呼叫資料錄集的 **Open** 成員函式時，**Open** 會建構這種形式的最後一個 **SELECT** 陳述式：  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 `table-name` 是藉由呼叫 `GetDefaultSQL` 所取得的，而 `rfx-field-list` 是從 `DoFieldExchange` 內的 RFX 函式呼叫所取得的。  除非您在執行階段以覆寫版本進行取代，否則這會是您得到的 **SELECT** 陳述式，但是您仍可用參數或篩選條件來修改預設的陳述式。  
  
> [!NOTE]
>  如果您指定包含 \(或能包含\) 空格的資料行名稱，就必須將該名稱放置在方括弧內。  例如，名稱 "First Name" 應該是 "\[First Name\]"。  
  
 若要覆寫預設的 **SELECT** 陳述式，請在呼叫 **Open** 時傳遞一個包含完整 **SELECT** 陳述式的字串。  資料錄集會使用您所提供的字串，而不自行建構其預設字串。  替代陳述式若包含 **WHERE** 子句，便請不要在 **m\_strFilter** 內指定篩選條件，以防同時出現兩個篩選條件陳述式。  同樣的，如果您的替代陳述式包含 **ORDER BY** 子句，請不要指定 `m_strSort` 內的排序，以免擁有兩個排序陳述式。  
  
> [!NOTE]
>  如果您在篩選條件中使用常值字串 \(或 SQL 陳述式的其他部分\)，您可能必須使用 DBMS 特定的常值前置字元和常值後置字元來「括住」這樣的字串 \(放在特定的分隔符號內\)。  
  
 視 DBMS 而定，您可能也會遭遇到作業上的特殊語法需求，例如外部聯結 \(Outer Join\)。  使用 ODBC 函式自您的驅動程式取得 DBMS 的資訊。  例如，對如 **SQL\_VARCHAR** 的特別資料型別呼叫 **::SQLGetTypeInfo**，以便要求 **LITERAL\_PREFIX** 和 **LITERAL\_SUFFIX** 字元。  如果您正在寫入與資料庫無關的程式碼，請參閱 MSDN Library 光碟片上《ODBC SDK 程式設計人員參考》內的附錄 C 的詳細語法資訊。  
  
 除非您傳遞自訂的 SQL 陳述式，否則資料錄集物件會建構用來選取資料錄的 SQL 陳述式。  這個動作的做法主要是根據您在 **Open** 成員函式的 `lpszSQL` 參數內傳遞的值。  
  
 SQL **SELECT** 陳述式的一般形式是：  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 將 **DISTINCT** 關鍵字加入資料錄集的 SQL 陳述式的一種方法，是在 `DoFieldExchange` 內的第一個 RFX 函式呼叫中嵌入此關鍵字。  例如：  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  只有在資料錄集開啟為唯讀時才能使用這個技術。  
  
## 覆寫 SQL 陳述式  
 下表內容說明 **Open** 的 `lpszSQL` 參數的可能性。  表格內的案例將說明於表格之後。  
  
 **lpszSQL 參數和產生的 SQL 字串**  
  
|案例|您在 lpszSQL 中傳遞什麼|產生的 SELECT 陳述式|  
|--------|----------------------|--------------------|  
|1|**NULL**|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> `CRecordset::Open` 呼叫 `GetDefaultSQL` 以取得資料表名稱。  根據 `GetDefaultSQL` 傳回的內容而定，產生的字串會是案例 2 到 5 的其中一種。|  
|2|任一資料表名稱|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> 欄位清單是取自 `DoFieldExchange` 內的 RFX 陳述式。  若 **m\_strFilter** 和 `m_strSort` 不是空的，便會加入 **WHERE** 和 \(或\) **ORDER BY** 子句。|  
|3 \*|不含 **WHERE** 或 **ORDER BY** 子句的完整 **SELECT** 陳述式|如所傳遞的。  若 **m\_strFilter** 和 `m_strSort` 不是空的，便會加入 **WHERE** 和 \(或\) **ORDER BY** 子句。|  
|4 \*|包含 **WHERE** 和 \(或\) **ORDER BY** 子句的完整 **SELECT** 陳述式|如所傳遞的。  **m\_strFilter** 和 \(或\) `m_strSort` 必須維持空白，否則會產生二個篩選條件和 \(或\) 排序陳述式。|  
|5 \*|預存程序呼叫|如所傳遞的。|  
  
 \* `m_nFields` 必須小於或等於 **SELECT** 陳述式內所指定的資料行數。  **SELECT** 陳述式內的指定的每個資料行之資料型別，必須與對應的 RFX 輸出資料行之資料型別相同。  
  
### 案例 1：lpszSQL \= NULL  
 資料錄集選取是將根據 `CRecordset::Open` 呼叫 `GetDefaultSQL` 時的傳回值而有所不同。  案例 2 到 5 說明可能出現的字串。  
  
### 案例 2：lpszSQL \= 資料表名稱  
 資料錄集使用資料錄欄位交換 \(RFX\)，從資料錄集類別的 `DoFieldExchange` 覆寫中的 RFX 函式呼叫中所提供的資料行名稱，來建立資料行清單。  若您已使用精靈宣告資料錄集類別，這個案例的結果會和案例 1 的結果相同 \(條件是您需傳遞在精靈內指定的相同資料表名稱\)。  如果您未使用精靈來寫入類別，則案例 2 會是建構 SQL 陳述式最簡單的方式。  
  
 下列範例所建構的 SQL 陳述式，會從 MFC 資料庫應用程式選取資料錄。  在架構呼叫 `GetDefaultSQL` 成員函式之後，函式會傳回資料表的名稱 `SECTION`。  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 為取得 SQL **SELECT** 陳述式的資料行名稱，架構會呼叫 `DoFieldExchange` 成員函式。  
  
```  
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)  
{  
    pFX->SetFieldType(CFieldExchange::outputColumn);  
    RFX_Text(pFX, "CourseID", m_strCourseID);  
    RFX_Text(pFX, "InstructorID", m_strInstructorID);  
    RFX_Text(pFX, "RoomNo", m_strRoomNo);  
    RFX_Text(pFX, "Schedule", m_strSchedule);  
    RFX_Text(pFX, "SectionNo", m_strSectionNo);  
}  
```  
  
 完成時，SQL 陳述式看起來就像這樣：  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### 案例 3：lpszSQL \= SELECT\/FROM 陳述式  
 您要手動指定資料行清單，而非由 RFX 自動建構。  這種作法的使用時機：  
  
-   您想要指定 **SELECT** 之後的 **DISTINCT** 關鍵字。  
  
     您的資料行清單順序應該符合列於 `DoFieldExchange` 內資料行名稱和型別的相同順序。  
  
-   您有充分的理由手動地以 ODBC 函式 **::SQLGetData** 來擷取資料行值，而無須 RFX 來為您繫結和擷取資料行。  
  
     例如，您可能希望在分散應用程式之後，將應用程式使用者所加入的新資料行，容納至資料庫資料表中。  您需加入那些在使用精靈宣告類別時仍未知的額外欄位資料成員。  
  
     您的資料行清單順序應該符合列於 `DoFieldExchange` 內資料行名稱和型別的相同順序，之後接續手動繫結的資料行名稱。  如需詳細資訊，請參閱[資料錄集：動態地繫結資料行 \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。  
  
-   您想要在 **FROM** 子句內指定多個表格來聯結資料表。  
  
     如需詳細資訊與範例，請參閱[資料錄集：執行聯結 \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)。  
  
### 案例 4：lpszSQL \= SELECT\/FROM 加上 WHERE 和 \(或\) ORDER BY  
 您可以指定所有項目：資料行清單 \(根據 `DoFieldExchange` 內的 RFX 呼叫\)、資料表清單和 **WHERE** 和 \(或\) **ORDER BY** 子句的內容。  若您依照這種方式指定 **WHERE** 和 \(或\) **ORDER BY** 子句，請不要使用 **m\_strFilter** 或 `m_strSort`。  
  
### 案例 5：lpszSQL \= 預存程序呼叫  
 若您需要呼叫預先定義查詢 \(例如 Microsoft SQL Server 資料庫內的預存程序\)，就必須在傳遞至 `lpszSQL` 的字串中寫入 **CALL** 陳述式。  精靈並不支援為呼叫預先定義查詢的資料錄集類別宣告。  並非所有的預先定義查詢都會傳回資料錄。  
  
 如果預先定義查詢沒有傳回資料錄，您可直接使用 `CDatabase` 成員函式 `ExecuteSQL`。  針對會傳回資料錄的預先定義查詢，您也必須為此程序所傳回的資料行，手動寫入 `DoFieldExchange` 內的 RFX 呼叫。  RFX 和預先定義查詢一樣，必須有相同的順序，並傳回相同的型別。  如需詳細資訊，請參閱[資料錄集：宣告預先定義查詢的類別 \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)。  
  
## 請參閱  
 [SQL：SQL 和 C\+\+ 資料類型 \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL：製作直接的 SQL 呼叫 \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)