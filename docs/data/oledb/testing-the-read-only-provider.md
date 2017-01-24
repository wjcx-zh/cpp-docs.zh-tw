---
title: "測試唯讀提供者 | Microsoft Docs"
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
  - "OLE DB 提供者, 呼叫"
  - "OLE DB 提供者, 測試"
  - "測試提供者"
  - "測試, OLE DB 提供者"
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 測試唯讀提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為了測試提供者，您要有一個消費者。  如果消費者可和提供者配合使用，這將助益許多。  OLE DB 消費者樣板 \(Consumer Template\) 是 OLE DB 周圍的小型包裝函式，並可搭配使用提供者 COM 物件。  由於原始程式碼隨附於消費者樣板，因此您可輕鬆地使用這些原始程式碼來偵錯提供者。  消費者樣板可快速地開發消費者應用程式並使程式更小巧。  
  
 本主題範例將為一個測試消費者，建立預設的 MFC 應用程式精靈應用程式。  測試應用程式是加入 OLE DB 消費者樣板程式碼的簡單對話方塊。  
  
### 若要建立測試應用程式  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[專案類型\] 窗格中選取 \[**Visual C\+\+ 專案**\] 資料夾。  在 \[樣板\] 窗格中選取 \[**MFC 應用程式**\]。  
  
3.  輸入 **TestProv** 做為專案名稱，然後按一下 \[**確定**\]。  
  
     將出現 MFC 應用程式精靈。  
  
4.  在 \[**應用程式類型**\] 頁面中選取 \[對話方塊架構\]。  
  
5.  在 \[**進階功能**\] 頁面選取 \[Automation\]，然後按一下 \[完成\]。  
  
> [!NOTE]
>  如果您在 **CTestProvApp::InitInstance** 加入 **CoInitialize**，應用程式就不需要 Automation 支援。  
  
 您可以在資源檢視中選取 TestProv 對話方塊 \(IDD\_TESTPROV\_DIALOG\) 來檢視和編輯。  放置兩個清單方塊，一個是為了資料列集的每個字串，另一個是為了對話方塊字串所設置。  若要關閉這兩個清單方塊的排序屬性，可選取清單方塊，然後按 ALT\+Enter，按一下 \[樣式\] 標籤，並清除 \[排序\] 核取方塊。  此外，可將 \[執行\] 按鈕放在對話方塊中來擷取檔案。  已經完成的 TestProv 對話方塊應該有兩個清單方塊，分別標為 "String 1" 和 "String 2"，並且還具有 \[**確定**\]、\[取消\] 和 \[執行\] 按鈕。  
  
 開啟對話方塊類別的標頭檔 \(在此例中為 TestProvDlg.H\)。  將下列程式碼加入至標頭檔 \(在任何類別宣告之外\)：  
  
```  
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
class CProvider   
{  
// Attributes  
public:  
   char   szField1[16];  
   char   szField2[16];  
  
   // Binding Maps  
BEGIN_COLUMN_MAP(CProvider)  
   COLUMN_ENTRY(1, szField1)  
   COLUMN_ENTRY(2, szField2)  
END_COLUMN_MAP()  
};  
```  
  
 這段程式碼表示了可定義資料列集將出現的資料行之使用者資料錄。  當用戶端呼叫 **IAccessor::CreateAccessor** 時，會使用這些項目來指定要繫結哪些資料行。  OLE DB 消費者樣板也可讓您動態繫結資料行。  COLUMN\_ENTRY 巨集為用戶端版本的 PROVIDER\_COLUMN\_ENTRY 巨集。  兩個 COLUMN\_ENTRY 巨集指定了兩個字串的序數、型別、長度和資料成員。  
  
 按下 CTRL，並按兩下 \[執行\] 按鈕，來為 \[執行\] 按鈕加入處理函式。  將下列程式碼放入函式中：  
  
```  
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider> > table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
      return;  
  
   if (session.Open(source) != S_OK)  
      return;  
  
   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
      return;  
  
   while (table.MoveNext() == S_OK)  
   {  
      m_ctlString1.AddString(table.szField1);  
      m_ctlString2.AddString(table.szField2);  
   }  
}  
```  
  
 `CCommand`、`CDataSource` 和 `CSession` 類別全都屬於 OLE DB 消費者樣板。  每個類別都模仿提供者的一個 COM 物件。  `CCommand` 物件會以標頭檔中宣告的 `CProvider` 類別做為樣板參數。  `CProvider` 參數表示您會用來存取提供者資料的繫結。  這個資料來源、工作階段和命令的 `Open` 程式碼:  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 開啟每個類別的程式碼列會在提供者內建立每個 COM 物件。  若要尋找提供者，請使用提供者的 ProgID。  您可自系統登錄取得 ProgID，或在 MyProvider.rgs 檔內尋找 \(開啟提供者目錄，並搜尋 ProgID 機碼\)。  
  
 MyProv 範例內包含 myData.txt 檔。  若要建立您自己的檔案，請使用編輯器，並輸入偶數的字串，每個字串之間都要按 ENTER。  如果您移動了檔案，請變更路徑。  
  
 在 `table.Open` 程式碼行中傳入字串 "c:\\\\samples\\\\myprov\\\\MyData.txt"。  如果您逐步執行 `Open` 呼叫，就會看到這個字串傳入提供者的 `SetCommandText` 方法內。  請注意，`ICommandText::Execute` 方法會使用該字串。  
  
 若要擷取資料，請在資料表上呼叫 `MoveNext`。  `MoveNext` 會呼叫 **IRowset::GetNextRows**、`GetRowCount` 和 `GetData` 函式。  若已經沒有資料列 \(也就是說，目前資料列集的位置大於 `GetRowCount`\)，迴圈 \(Loop\) 就會結束：  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 請注意，沒有資料列時，提供者便會傳回 **DB\_S\_ENDOFROWSET**。  **DB\_S\_ENDOFROWSET** 值不能是個錯誤。  您應該要一直檢查 `S_OK`，來取消資料擷取迴圈，且不要使用 SUCCEEDED 巨集。  
  
 現在您應可建置 \(Build\) 此程式並測試。  
  
## 請參閱  
 [增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)