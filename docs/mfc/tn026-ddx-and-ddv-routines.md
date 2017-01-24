---
title: "TN026：DDX 和 DDV 常式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DDX"
  - "DDV"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDV (對話方塊資料驗證), 程序"
  - "DDX (對話資料交換), 程序"
  - "TN026"
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN026：DDX 和 DDV 常式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。  因此，有些程序和主題可能已過期或不正確。  如需最新資訊，建議您在線上文件索引中搜尋相關的主題。  
  
 這個會描述對話資料交換 \(Dialog Data Exchange，DDX\) 和對話資料驗證 \(DDV\) 結構。  它也說明如何撰寫 DDX\_ 或 DDV\_ 程序，以及如何擴充 ClassWizard 使用自己的常式。  
  
## 對話資料交換概觀  
 所有對話資料函式完成與 C\+\+ 程式碼。  沒有特殊資源或不需要什麼特別的巨集。  這個機制的核心是在每個類別覆寫做對話資料交換和驗證的虛擬函式。  永遠會以這種形式:  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);    // call base class  
  
    //{{AFX_DATA_MAP(CMyDialog)  
        <data_exchange_function_call>  
        <data_validation_function_call>  
    //}}AFX_DATA_MAP  
}  
```  
  
 特殊格式 AFX 註解允許 ClassWizard 尋找和編輯此函式中的程式碼。  程式碼與 ClassWizard 相容應該放置在特殊格式註解外。  
  
 在上述範例中， \<data\_exchange\_function\_call\> 表單:  
  
```  
DDX_Custom(pDX, nIDC, field);  
```  
  
 然後 \<data\_validation\_function\_call\> 是選擇性的和表單:  
  
```  
DDV_Custom(pDX, field, ...);  
```  
  
 多個 DDX\_\/DDV\_ 每次 `DoDataExchange` 函式可能包括。  
  
 為所有對話資料交換常式和對話資料驗證常式清單參閱「afxdd\_.h」隨附 MFC。  
  
 對話資料是:在 **CMyDialog** 類別的成員資料。  它在類似的結構或的任何未儲存。  
  
## 備註  
 雖然我們稱此對話資料，所有功能可以在衍生自 `CWnd` 的類別並不限於對話方塊。  
  
 原始資料在 Standard C\+\+ 建構函式設定，通常在具有 `//{{AFX_DATA_INIT` 和 `//}}AFX_DATA_INIT` 的註解區塊。  
  
 `CWnd::UpdateData` 是在呼叫前後進行初始化和錯誤處理對 `DoDataExchange`的作業。  
  
 您可以隨時呼叫 `CWnd::UpdateData` 執行資料交換和驗證。  預設為 `UpdateData`\(true\) 在預設 `CDialog::OnOK` 處理常式和 `UpdateData`\(false\) 在預設 `CDialog::OnInitDialog`呼叫。  
  
 DDV\_ 常式應該緊接在該欄位 *的*DDX\_ 常式。  
  
## 它的運作方式?  
 您不需要了解下列才能使用對話資料。  不過，了解這項處理在幕後作業可協助您撰寫交換或驗證程序。  
  
 `DoDataExchange` 成員函式非常類似 `Serialize` 成員函式 \(它會取得或設定從外部表單 \(在此情況下在對話方塊上控制項的資料負責\) 從\/至類別中的成員資料。  `pDX` 參數是對資料交換內容類似 `CArchive` 參數的 `CObject::Serialize`。  `pDX` \( `CDataExchange` 物件\) 有方向旗標很像 `CArchive` 有方向旗標:  
  
-   如果 **\!m\_bSaveAndValidate**，然後載入資料狀態的控制項。  
  
-   如果 `m_bSaveAndValidate`，則將會從控制項的資料狀態。  
  
 只驗證發生，當 `m_bSaveAndValidate` 設定。  `m_bSaveAndValidate` 的值取決於 `CWnd::UpdateData`的 BOOL 參數。  
  
 有三個有趣的 `CDataExchange` 成員:  
  
-   `m_pDlgWnd`:這個視窗 \(通常對話\) 包含控制項。  這是為了防止全域函式都必須傳遞" this」對每個 DDX\/DDV 常式 DDX\_ 和 DDV\_ 的呼叫端。  
  
-   `PrepareCtrl`和 `PrepareEditCtrl`:對話方塊控制項為資料交換做準備。  存放區設定焦點的控制項，如果驗證失敗。  `PrepareCtrl` 為 nonedit 控制項使用，且 `PrepareEditCtrl` 為編輯控制項使用。  
  
-   **Fail**:呼叫在引發警告的訊息方塊後輸入錯誤。  這個常式會還原焦點至最後一個控制項 \(如 `PrepareCtrl`或`PrepareEditCtrl`\) 上次呼叫時會擲回例外狀況。  此成員函式可能會 DDX\_ 和 DDV\_ 常式呼叫。  
  
## 使用者擴充功能。  
 有幾個方式擴充預設 DDX\/DDV 機制。  您可以：  
  
-   加入新的資料型別。  
  
    ```  
    CTime  
    ```  
  
-   加入新的交換程序 \(DDX\_???\)。  
  
    ```  
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);  
    ```  
  
-   加入新的驗證程序 \(DDV\_???\)。  
  
    ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);  
    // make sure time is in the future or past  
    ```  
  
-   您可以任意運算式驗證程序。  
  
    ```  
    DDV_MinMax(pDX, age, 0, m_maxAge);  
    ```  
  
    > [!NOTE]
    >  這類任意運算式不是 ClassWizard 編輯也不應該將特殊格式註解外 \(\/\/ {{AFX\_DATA\_MAP \(CMyClass\)\)。  
  
 有 **DoDialogExchange** 成員函式包含條件式或任何其他有效 C\+\+ 陳述式具有混合的交換和驗證函式呼叫。  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX, IDC_SEX, m_bFemale);  
DDX_Text(pDX, IDC_EDIT1, m_age);  
//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);  
else  
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);  
```  
  
> [!NOTE]
>  如先前所述，這類程式碼並不是由 ClassWizard 編輯，而且只能在特殊格式註解外。  
  
## ClassWizard 支援  
 ClassWizard 可讓您將您的 DDX\_ 和 DDV\_ 常式支援 DDX\/DDV 自訂的子集 ClassWizard 使用者介面。  如果您想要重複使用特殊 DDX 和 DDV 常式在專案或在許多專案，這樣做只花費有利。  
  
 若要這樣做，特別是項目會在 DDX.CLW \(舊版 Visual C\+\+ 中 APSTUDIO.INI 儲存資訊\) 或在專案 .CLW 檔案。  特殊項目則會將專案 .CLW 檔案的一般資訊\] \[部分或在 DDX.CLW 檔案的 ExtraDDX \[\] 部分在\\ Program Files \\ Microsoft Visual Studio \\ Visual C\+\+ \\ Bin 目錄中。  如果不存在，您可能需要建立 DDX.CLW 檔案。  如果您在某個專案計劃只使用自訂 DDX\_\/DDV\_ 常式，請將項目加入至項目 .CLW 檔案的一般資訊\] \[部分。  如果您打算在多個專案的常式，將項目加入至 DDX.CLW \[\] ExtraDDX 部分。  
  
 這些特殊輸入一般格式為:  
  
```  
ExtraDDXCount=n  
```  
  
 n 位置是數字 ExtraDDX?的下一行中  
  
```  
ExtraDDX?=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 在哪裡?是第 1 – n 表示哪些 DDX 項目定義的清單。  
  
 每個欄位都由分隔「; 」字元。  欄位及其用途如下。  
  
 \<索引鍵\>  
 \= 表示唯一字元清單的對話方塊控制項這個變數型別允許。  
  
 E \= 編輯  
  
 C \= 兩種狀態的核取方塊。  
  
 c \= 三種狀態的核取方塊。  
  
 R \= 第一選項按鈕群組中  
  
 L \= nonsorted 清單方塊  
  
 左 \= 排序的清單方塊  
  
 M out \= 下拉式方塊 \(與編輯項目\)  
  
 N \= nonsorted 下拉清單  
  
 n \= 排序的下拉清單  
  
 這對於 DDX 常式通常使用 SHIFT 「控制」屬性的 1 \=，如果 DDX 插入應該加入至清單開頭 \(預設是加入至尾端\)。  
  
 \<vb 索引鍵\>  
 這個欄位會在這個 16 位元產品只適用於 VBX 控制 \(VBX 控制項處於 32 位產品不支援\)  
  
 \<提示\>  
 將字串中屬性下拉式方塊 \(未參考\)  
  
 \<type\>  
 型別的唯一識別項可以分散在標頭檔。  在上面的範例我們的中與 DDX\_Time，這會設定為 CTime。  
  
 \<vb 索引鍵\>  
 不使用這個版本，並且應該永遠保持空白。  
  
 \<initValue\>  
 初始值— 0 或空白。  如果是空白的，則使用行在\/\/不會寫入{{實作檔 \(Implementation File\) 的 AFX\_DATA\_INIT 部分。  應為有建構函式可確保正確初始化的 C\+\+ 物件使用空白項目 \(例如 `CString`， `CTime`，依此類推\)。  
  
 \<DDX\_Proc\>  
 DDX\_ 程序的唯一識別項。  C\+\+ 函式名稱在 DDX\_Proc\> 識別項的開頭必須是「DDX\_，」，但是「 \<DDX\_」。  在上面的範例中， \<DDX\_Proc\> 識別項是時間。  當 ClassWizard 撰寫函式呼叫到實作檔中{{AFX\_DATA\_MAP 部分，因此附加這個名稱 DDX\_，因而到達 DDX\_Time。  
  
 \<註解\>  
 註解會顯示變數的對話方塊與這個 DDX。  將您要在這裡的所有文字和通常描述 DDX\/DDV 對執行作業的事。  
  
 \<DDV\_Proc\>  
 輸入的 DDV 部分是選擇性的。  並非所有的 DDX 常式有對應的 DDV 常式。  通常，包括驗證階段做為傳輸的整數部分更方便。  這通常是，當您的 DDV 常式不需要任何參數時，，因為 ClassWizard 不支援 DDV 常式不帶任何參數。  
  
 \<arg\>  
 DDV\_ 程序的唯一識別項。  C\+\+ 函式名稱在 DDX\_Proc\> 識別項的開頭必須是「， DDV\_」，但是「 \<DDX\_」。  
  
 後面接著 1 或 2 DDV 引數:  
  
 \<promptX\>  
 將的字串會在編輯項目上 \(與 & 為快速鍵\)  
  
 \<fmtX\>  
 arg 型別的格式字元，。  
  
 \! \= int  
  
 U \= 未簽署  
  
 D \= long int \(即長度\)  
  
 U \= 長時間未帶正負號 \(即 DWORD\)  
  
 f \= 浮動  
  
 F \= 雙  
  
 s \= 字串  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)