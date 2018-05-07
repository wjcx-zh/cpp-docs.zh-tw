---
title: 測試唯讀提供者 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 703d33f44fae534b206050e85086edb1ccc816f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="testing-the-read-only-provider"></a>測試唯讀提供者
若要測試的提供者，您需要取用者。 如果取用者可以比對與提供者，它可幫助。 OLE DB 消費者樣板是 OLE DB 的精簡型包裝函式，而且與提供者 COM 物件相符。 來源隨附的取用者範本，因為很容易進行偵錯與它們的提供者。 消費者樣板也是開發取用者應用程式非常小且更快速的方式。  
  
 本主題中的範例會建立預設的 MFC 應用程式精靈應用程式測試取用者。 測試應用程式是以 OLE DB 消費者範本程式碼加入簡單的對話方塊。  
  
### <a name="to-create-the-test-application"></a>若要建立測試應用程式  
  
1.  按一下 [ **檔案** ] 功能表上的 [ **新增**]，然後按一下 [ **專案**]。  
  
2.  在 [專案類型] 窗格中，選取**Visual c + + 專案**資料夾。 在 [範本] 窗格中，選取**MFC 應用程式**。  
  
3.  專案名稱輸入**TestProv**，然後按一下 **確定**。  
  
     MFC 應用程式精靈 隨即出現。  
  
4.  在**應用程式類型**頁面上，選取**對話方塊架構**。  
  
5.  在**進階功能**頁面上，選取**自動化**，然後按一下 **完成**。  
  
> [!NOTE]
>  如果您加入應用程式不需要自動化支援**CoInitialize**中**CTestProvApp::InitInstance**。  
  
 您可以檢視和編輯 TestProv 對話方塊 (IDD_TESTPROV_DIALOG) 在 資源檢視中選取。 將兩個清單方塊中，一個用於每個字串中的資料列集，放在對話方塊中。 關閉的排序屬性，讓同時按下 ALT + Enter 在選取清單方塊時，按一下清單方塊**樣式**索引標籤，然後清除**排序**核取方塊。 此外，放置**執行**來擷取檔案對話方塊上的按鈕。 完成的 TestProv 對話方塊應該有兩個清單方塊標示為 「 字串 1 」 和 「 字串 2"，分別;它也有**確定**，**取消**，和**執行**按鈕。  
  
 開啟對話方塊類別 （在此案例的 TestProvDlg.h) 的標頭檔。 將下列程式碼加入至標頭檔 （之外的任何類別宣告）：  
  
```cpp
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
  
 此代碼表示定義欄將會在資料列集的使用者記錄。 當用戶端呼叫**iaccessor:: Createaccessor**，它會使用這些項目指定要繫結的資料行。 OLE DB 消費者樣板也可讓您動態繫結資料行。 COLUMN_ENTRY 巨集是 PROVIDER_COLUMN_ENTRY 巨集的用戶端版本。 兩個 COLUMN_ENTRY 巨集指定序數、 兩個字串的類型、 長度和資料成員。  
  
 加入處理常式函式的**執行**按住 ctrl 鍵並按兩下按鈕**執行** 按鈕。 下列程式碼置於函式：  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
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
  
 `CCommand`， `CDataSource`，和`CSession`所有屬於 OLE DB 消費者樣板的類別。 每個類別會模擬 COM 物件提供者中。 `CCommand`物件會使用`CProvider`標頭檔，做為範本參數中所宣告的類別。 `CProvider`參數表示您用來從提供者存取資料繫結。 以下是`Open`資料來源、 工作階段和命令的程式碼：  
  
```  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
 若要開啟每個類別建立每個 COM 物件提供者中。 若要尋找的提供者，使用提供者的 ProgID。 從系統登錄或查詢 MyProvider.rgs 檔案中，您可以取得 ProgID （開啟提供者的目錄和 ProgID 的索引鍵搜尋）。  
  
 MyData.txt 檔案隨附於 MyProv 範例。 若要建立您自己的檔案，使用編輯器，並輸入字串，按 ENTER，每個字串之間的偶數。 如果您移動的檔案，變更路徑名稱。  
  
 傳遞字串"c:\\\samples\\\myprov\\\MyData.txt 」 中`table.Open`列。 如果您將逐步執行`Open`呼叫時，您會看到這個字串會傳遞至`SetCommandText`提供者中的方法。 請注意，`ICommandText::Execute`使用該字串的方法。  
  
 若要擷取的資料，呼叫`MoveNext`資料表上。 `MoveNext` 呼叫**irowset:: Getnextrows**， `GetRowCount`，和`GetData`函式。 當沒有任何多個資料列 (亦即，資料列集的目前位置是大於`GetRowCount`)，迴圈會終止：  
  
```  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
 請注意，沒有其他資料列時，提供者就會傳回**DB_S_ENDOFROWSET**。 **DB_S_ENDOFROWSET**值不是錯誤。 您應該永遠會檢查對`S_OK`取消資料擷取迴圈，而不使用 SUCCEEDED 巨集。  
  
 您現在應該能夠建置並測試的程式。  
  
## <a name="see-also"></a>另請參閱  
 [增強簡單唯讀提供者](../../data/oledb/enhancing-the-simple-read-only-provider.md)