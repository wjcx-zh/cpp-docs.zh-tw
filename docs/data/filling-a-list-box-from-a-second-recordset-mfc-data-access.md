---
title: "以第二個記錄集填入清單方塊 (MFC 資料存取) | Microsoft Docs"
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
  - "CComboBox 類別, 從第二資料錄集填入填滿物件"
  - "CListCtrl 類別, 從第二資料錄集填入"
  - "下拉式方塊 [C++], 從第二資料錄集填入"
  - "DAO 資料錄集"
  - "DAO 資料錄集, 填入清單方塊或下拉式方塊"
  - "填入清單或下拉式方塊"
  - "清單方塊, 從第二資料錄集填入"
  - "資料錄檢視中的多個資料錄集"
  - "ODBC 資料錄集 [C++], 填入清單方塊或下拉式方塊"
  - "資料錄檢視, 填入清單方塊"
  - "資料錄集 [C++], 填入清單方塊或下拉式方塊"
ms.assetid: 360c0834-da6b-4dc0-bcea-80e9acd611f0
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 以第二個記錄集填入清單方塊 (MFC 資料存取)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

根據預設，資料錄檢視與單一資料錄集物件相關聯，其欄位會對應至資料錄檢視的控制項。  有時您可能想要將清單方塊或下拉式方塊控制項置於資料錄檢視中，並填入第二個資料錄集物件中的值。  使用者可以使用清單方塊來選取要在資料錄檢視中顯示的新類別的資訊。  本主題將說明如何和何時執行該操作。  
  
> [!TIP]
>  請注意，從資料來源填入下拉式方塊或清單方塊可能會比較緩慢。  請採取預防措施，防止嘗試從具有大量資料錄的資料錄集填入控制項。  
  
 本主題的模型包含主要資料錄集，用來填入您表單的控制項，而第二個資料錄集則填入清單方塊或下拉式方塊。  從清單方塊中選取字串，會導致您的程式根據選取的項目重新查詢主要資料錄集。  下列程序使用下拉式方塊，但也同樣適用於清單方塊。  
  
#### 從第二個資料錄集填入下拉式方塊或清單方塊  
  
1.  建立資料錄集物件 \(ODBC 為 [CRecordset](../mfc/reference/crecordset-class.md)，DAO 為[CDaoRecordset](../mfc/reference/cdaorecordset-class.md)\)。  
  
2.  取得指向下拉式方塊控制項之 [CComboBox](../mfc/reference/ccombobox-class.md) 物件的指標。  
  
3.  清空下拉式方塊的所有先前內容。  
  
4.  在資料錄集中的所有記錄之間移動，呼叫 [CComboBox::AddString](../Topic/CComboBox::AddString.md) 以取得目前資料錄中要加入下拉式方塊的每一個字串。  
  
5.  初始化下拉式方塊中的選取項目。  
  
```  
void CSectionForm::OnInitialUpdate()  
{  
    // ...  
  
    // Fill the combo box with all of the courses  
    CENROLLDoc* pDoc = GetDocument();  
    if (!pDoc->m_courseSet.Open())  
        return;  
  
    // ...  
  
    m_ctlCourseList.ResetContent();  
    if (pDoc->m_courseSet.IsOpen())  
    {   
        while (!pDoc->m_courseSet.IsEOF() )  
        {  
            m_ctlCourseList.AddString(  
                pDoc->m_courseSet.m_CourseID);  
            pDoc->m_courseSet.MoveNext();  
        }  
    }  
    m_ctlCourseList.SetCurSel(0);  
}  
```  
  
 這個函式會使用第二個資料錄集 `m_courseSet`，其中包含每項課程提供的資料錄，以及 `CComboBox` 控制項 `m_ctlCourseList`，其儲存在資料錄檢視類別中。  
  
 此函式會從文件取得 `m_courseSet` 並開啟它。  然後它會清空 `m_ctlCourseList` 並捲動 `m_courseSet`。  針對每一個資料錄，此函式會呼叫下拉式方塊的 `AddString` 成員函式，從資料錄加入課程 ID 值。  最後，程式碼會設定下拉式方塊的選取項目。  
  
## 請參閱  
 [記錄檢視 \(MFC 資料存取\)](../data/record-views-mfc-data-access.md)   
 [ODBC 驅動程式清單](../data/odbc/odbc-driver-list.md)