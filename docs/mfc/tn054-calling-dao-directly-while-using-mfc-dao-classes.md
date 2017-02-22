---
title: "TN054：在使用 MFC DAO 類別時直接呼叫 DAO | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.dao"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DAO (資料存取物件), 與 MFC"
  - "DAO (資料存取物件), 直接呼叫"
  - "DAO (資料存取物件), 安全性"
  - "MFC [C++], DAO 和"
  - "密碼 [C++], 呼叫 DAO"
  - "安全性 [MFC]"
  - "安全性 [MFC], DAO"
  - "TN054"
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# TN054：在使用 MFC DAO 類別時直接呼叫 DAO
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  從 Visual C\+\+ .NET 開始，Visual C\+\+ 環境和精靈不再支援 DAO \(但該版本中仍包含 DAO 類別，您仍然可以使用這些類別\)。  Microsoft 建議您在新的專案使用 [OLE DB 樣板](../data/oledb/ole-db-templates.md) 或 [ODBC 和 MFC](../data/odbc/odbc-and-mfc.md) 。  請在維護現有應用程式時再使用 DAO。  
  
 當使用 MFC DAO 資料庫類別時，可能會直接使用 DAO 的情況是必要的。  一般而言，不會是這種情況，不過， MFC 提供一些 Helper 機制有助於製作直接呼叫 DAO 簡單，當合併使用 MFC 類別與直接呼叫 DAO 時。  對 MFC DAO Managed 物件的方法的直接呼叫 DAO 需要少數程式碼。  如果您需要建立和使用未處理的 MFC DAO 物件，您必須透過實際在物件上呼叫 **Release** 會完成更多工作。  這個技術提示說明何時可以直接呼叫 DAO，以及 MFC Helper 可協助您和如何使用 DAO OLE 介面。  最後，這個附註提供示範如何的一些範例函式呼叫 DAO 直接 DAO 安全性功能的。  
  
## 何時會直接呼叫 DAO  
 製作直接呼叫 DAO 的最常見情況發生時，需要重新整理集合，或當您實作 MFC 時未包裝的功能。  MFC 中公開的最重要的功能是安全性。  如果您要實作安全性功能，您必須使用 DAO，使用者和群組直接物件。  除了安全性之外，還有 MFC 中只支援其他 DAO 功能。  這些包括資料錄集複製和資料庫複製功能以及一些晚加入至 DAO。  
  
## DAO 和 MFC 的實作的簡短概觀  
 MFC 的包裝 DAO 可使用 DAO 可藉由處理許多細節，讓您不必擔心小的事。  這包括 OLE、DAO 物件 \(特別是集合物件\)，錯誤檢查和提供強型別，更簡單的介面的建立和管理的初始化 \(沒有 **VARIANT** 或 `BSTR` 引數\)。  您可以直接呼叫 DAO 呼叫但仍要使用這些功能。  將所有程式碼必須是直接呼叫 DAO 呼叫所建立之所有物件的 **Release** 和不修改任何介面指標 MFC 可能依賴內部。  例如，在中，除非您了解 *所有* 內部細節，請不要開啟之 `CDaoRecordset` 物件的 **m\_pDAORecordset** 成員。  您可以使用，不過， **m\_pDAORecordset** 介面直接呼叫 DAO 取得欄位集合。  在這種情況下並不會修改 **m\_pDAORecordset** 成員。  當您完成使用物件時，您必須呼叫在欄位集合物件的 **Release** 。  
  
## 使 DAO 呼叫更加容易的 Helper 的描述  
 Helper 提供將呼叫 DAO 更加容易是內部 MFC DAO 資料庫類別使用相同的 Helper。  這些 Helper 用來檢查傳回碼，因此在進行直接呼叫 DAO，記錄時偵錯輸出，必要時，檢查潛在錯誤並擲回適當的例外狀況。  取得對應至這兩個協助程式之一的兩種基本的 Helper 函式和四個巨集。  最好的解譯是讀取程式碼。  請參閱 **DAO\_CHECK**和 **DAO\_CHECK\_ERROR**和 **DAO\_CHECK\_MEM**和 **DAO\_TRACE** 在 AFXDAO.H 看巨集，並參閱 **AfxDaoCheck** 和 **AfxDaoTrace** 在 DAOCORE.CPP。  
  
## 使用 DAO OLE 介面  
 每個物件的 OLE 介面 DAO 物件階層架構在標頭檔 DBDAOINT.H 定義，在\\ Program Files \\ Microsoft Visual Studio .NET 2003. \\ VC7 找到\\ Include 目錄。  這些介面提供可讓您管理整個 DAO 階層架構的方法。  
  
 對於許多 DAO 介面的方法，您將需要管理 `BSTR` 物件 \(用於 OLE Automation 的長度前置字元的字串\)。  `BSTR` 物件在 **VARIANT** 資料型別中通常會封裝。  MFC 類別從 **VARIANT**`COleVariant` 資料型別。  視您建立自己的 ANSI 或 Unicode 的專案， DAO 介面會傳回 ANSI 或 Unicode `BSTR`。  兩個巨集， **V\_BSTR** 和 **V\_BSTRT**，可確保是有用的 DAO 介面取得預期型別的 `BSTR` 。  
  
 **V\_BSTR** 中擷取 `COleVariant`**bstrVal** 的成員。  這個巨集，當您需要將 `COleVariant` 的內容加入至 DAO 介面的方法時，通常就會使用。  下列程式碼片段顯示宣告和實際用途使用 **V\_BSTR** 巨集 DAO DAOUser 介面的兩個方法:  
  
```  
COleVariant varOldName;  
COleVariant varNewName( _T("NewUser"), VT_BSTRT );  
  
// Code to assign pUser to a valid value omitted  
DAOUser *pUser = NULL;  
  
// These method declarations were taken from DBDAOINT.H  
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;  
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;  
  
DAO_CHECK( pUser->get_Name( &V_BSTR ( &varOldName ) ));  
DAO_CHECK( pUser->put_Name( V_BSTR ( &varNewName ) ));  
```  
  
 請注意在 `COleVariant` 建構函式使用指定的 `VT_BSTRT` 引數上面保證會在 `COleVariant` 的 ANSI `BSTR` ，如果建置您的應用程式版本 ANSI 和 Unicode `BSTR` 對您的應用程式 Unicode 版本。  這是什麼 DAO 預期。  
  
 另一個巨集， **V\_BSTRT**，根據組建類型中擷取 `COleVariant` 的 ANSI 或 Unicode **bstrVal** 成員 \(ANSI 或 Unicode\)。  下列程式碼示範如何從 `COleVariant` 擷取 `BSTR` 值至 `CString`:  
  
```  
COleVariant varName( _T( "MyName" ), VT_BSTRT );  
CString str = V_BSTRT( &varName );  
```  
  
 **V\_BSTRT** 巨集，以及開啟儲存於 `COleVariant`中的其他型別的其他技術搭配，在 DAOVIEW 範例所示範。  具體來說，這項轉譯在 **CCrack::strVARIANT** 方法執行。  這個方法，可能的話，轉譯 `COleVariant` 的值為 `CString`執行個體。  
  
## 直接呼叫的簡單範例至 DAO 的  
 當重新整理基礎 DAO 集合物件時，有必要條件可能會出現。  通常，這應該不是必要的，不過，它是一個簡單的程序，如果是必要的。  例如，當集合可能需要重新整理為，當在中建立新的 tabledefs 中多個使用者的多使用者的環境。  在這個案例中的 tabledefs 集合可能會變成過時。  若要重新整理集合，您必須呼叫特定集合物件的 **Refresh** 方法和檢查錯誤:  
  
```  
DAO_CHECK( pMyDaoDatabase->  
    m_pDAOTableDefs->Refresh( ) );  
```  
  
 請注意目前所有 DAO 集合物件介面是 MFC DAO 資料庫類別的未記載的實作詳細資料。  
  
## 使用 DAO 直接 DAO 安全性功能的  
 MFC DAO 資料庫類別不換行 DAO 安全性功能。  您必須呼叫 DAO 介面方法使用某個 DAO 安全性功能。  下列函式集系統資料庫然後變更使用者密碼。  這個函式呼叫其他三個函式後，來定義。  
  
```  
void ChangeUserPassword( )  
{  
   // Specify path to the Microsoft Access  
   // system database  
   CString strSystemDB =   
     _T( "c:\\Program Files\\MSOffice\\access\\System.mdw" );  
  
   // Set system database before MFC initilizes DAO  
   // NOTE: An MFC module uses only one instance   
   // of a DAO database engine object. If you have   
   // called a DAO object in your application prior   
   // to calling the function below, you must call   
   // AfxDaoTerm to destroy the existing database   
   // engine object. Otherwise, the database engine   
   // object already in use will be reused, and setting  
   // a system datbase will have no effect.  
   //  
   // If you have used a DAO object prior to calling   
   // this function it is important that DAO be   
   // terminated with AfxDaoTerm since an MFC  
   // module only gets one copy of the database engine   
   // and that engine will be reused if it hasn't been   
   // terminated. In other words, if you do not call   
   // AfxDaoTerm and there is currently a database   
   // initialized, setting the system database will   
   // have no affect.  
  
   SetSystemDB( strSystemDB );  
  
   // User name and password manually added  
   // by using Microsoft Access  
   CString strUserName = _T( "NewUser" );  
   CString strOldPassword = _T( "Password" );  
   CString strNewPassword = _T( "NewPassword" );  
  
   // Set default user so that MFC will be able  
   // to log in by default using the user name and   
   // password from the system database  
   SetDefaultUser( strUserName, strOldPassword );  
  
   // Change the password. You should be able to  
   // call this function from anywhere in your   
   // MFC application  
   ChangePassword( strUserName, strOldPassword,   
                   strNewPassword );  
  
   .  
   .  
   .  
  
}  
```  
  
 下四個範例示範如何:  
  
-   設定系統 DAO 資料庫 \(.MDW 檔案\)。  
  
-   設定預設使用者和密碼。  
  
-   變更使用者的密碼。  
  
-   變更 .MDB 檔案的密碼。  
  
### 設定系統資料庫  
 下面將會由應用程式使用的系統資料庫的範例函式。  這個函式，在任何其他 DAO 呼叫之前，必須呼叫。  
  
```  
// Set the system database that the   
// DAO database engine will use  
  
void SetSystemDB( CString & strSystemMDB )  
{  
   COleVariant varSystemDB( strSystemMDB, VT_BSTRT );  
  
   // Initialize DAO for MFC  
   AfxDaoInit( );  
   DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  
   ASSERT( pDBEngine != NULL );  
  
   // Call put_SystemDB method to set the   
   // system database for DAO engine  
   DAO_CHECK( pDBEngine->put_SystemDB( varSystemDB.bstrVal ) );  
}  
```  
  
### 設定預設使用者和密碼  
 若要設定預設使用者和密碼系統資料庫的，請使用下列函式:  
  
```  
void SetDefaultUser(CString & strUserName, CString & strPassword)  
{  
  COleVariant varUserName( strUserName, VT_BSTRT );  
  COleVariant varPassword( strPassword, VT_BSTRT );  
  
  DAODBEngine* pDBEngine = AfxDaoGetEngine( );  
  ASSERT( pDBEngine != NULL );  
  
  // Set default user:  
  DAO_CHECK( pDBEngine->put_DefaultUser( varUserName.bstrVal ) );  
  
  // Set default password:  
  DAO_CHECK( pDBEngine->put_DefaultPassword( varPassword.bstrVal ) );  
}  
```  
  
### 變更使用者密碼。  
 若要變更使用者密碼，請使用下列函式:  
  
```  
void ChangePassword( CString &strUserName,   
                     CString &strOldPassword,   
                     CString &strNewPassword )  
{  
   // Create (open) a workspace  
   CDaoWorkspace wsp;  
   CString strWspName = _T( "Temp Workspace" );  
  
   wsp.Create( strWspName, strUserName,  
               strOldPassword );  
   wsp.Append( );  
  
   // Determine how many objects there are  
   // in the Users collection  
   short nUserCount;  
   short nCurrentUser;  
   DAOUser *pUser  = NULL;  
   DAOUsers *pUsers = NULL;  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUser object:  
   DAO_CHECK( wsp.m_pDAOWorkspace->get_Users( &pUsers ) );  
  
   // Side-effect is implicit OLE AddRef( )   
   // on DAOUsers object  
    DAO_CHECK( pUsers->get_Count( &nUserCount ) );  
  
   // Traverse through the list of users   
   // and change password for the userid  
   // used to create/open the workspace  
   for( nCurrentUser = 0; nCurrentUser < nUserCount;  
        nCurrentUser++ )  
   {  
       COleVariant varIndex( nCurrentUser, VT_I2 );  
       COleVariant varName;  
  
       // Retrieve information for user nCurrentUser  
       DAO_CHECK( pUsers->get_Item( varIndex, &pUser ) );  
  
       // Retrieve name for user nCurrentUser  
       DAO_CHECK( pUser->get_Name( &V_BSTR( &varName ) ) );  
  
       CString strTemp = V_BSTRT( &varName );  
  
       // If there is a match, change the password  
       if( strTemp == strUserName )  
       {  
           COleVariant varOldPwd( strOldPassword,   
                                  VT_BSTRT );  
           COleVariant varNewPwd( strNewPassword,   
                                  VT_BSTRT );  
  
           DAO_CHECK( pUser->NewPassword( V_BSTR( &varOldPwd ),  
                      V_BSTR( &varNewPwd ) ) );  
  
           TRACE( "\t Password is changed\n" );  
       }  
   }  
  
   // Clean up: decrement the usage count  
   // on the OLE objects  
   pUser->Release( );  
   pUsers->Release( );  
  
   wsp.Close( );  
}  
```  
  
### 變更 .MDB 檔案的密碼。  
 若要變更 .MDB 檔案的密碼，請使用下列函式:  
  
```  
void SetDBPassword( LPCTSTR pDB, LPCTSTR pszOldPassword, LPCTSTR pszNewPassword )  
{  
   CDaoDatabase db;  
   CString strConnect( _T( ";pwd=" ) );  
  
   // the database must be opened as exclusive  
   // to set a password  
   db.Open( pDB, TRUE, FALSE,   
            strConnect + pszOldPassword );  
  
   COleVariant NewPassword( pszNewPassword, VT_BSTRT ),  
               OldPassword( pszOldPassword, VT_BSTRT );  
  
   DAO_CHECK( db.m_pDAODatabase->NewPassword( V_BSTR( &OldPassword ),  
              V_BSTR( &NewPassword ) ) );  
  
   db.Close();  
}  
```  
  
## 請參閱  
 [依編號顯示的技術提示](../mfc/technical-notes-by-number.md)   
 [依分類區分的技術提示](../mfc/technical-notes-by-category.md)