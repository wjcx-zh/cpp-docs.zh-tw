---
title: TN054：在使用 MFC DAO 類別時直接呼叫 DAO
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
ms.openlocfilehash: 0eb9daf156f51ecb4eb1e6fdc721b34878a43351
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303427"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054：在使用 MFC DAO 類別時直接呼叫 DAO

> [!NOTE]
> DAO 會與 Access 資料庫搭配使用，並透過 Office 2013 支援。 DAO 3.6 是最後的版本，被視為已淘汰。 視覺C++環境和嚮導不支援 dao （雖然包含 dao 類別，但您仍然可以使用它們）。 Microsoft 建議您針對新專案使用[OLE DB 範本](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md) 。 您應該只在維護現有的應用程式時使用 DAO。

使用 MFC DAO 資料庫類別時，可能有一些情況需要直接使用 DAO。 通常不會發生這種情況，但 MFC 已提供一些 helper 機制，可在結合 MFC 類別與直接 DAO 呼叫的使用時，簡化直接 DAO 呼叫的過程。 對 MFC 管理的 DAO 物件的方法進行直接的 DAO 呼叫，應該只需要幾行程式碼。 如果您需要建立並使用*不*受 MFC 管理的 DAO 物件，您必須實際呼叫物件上的 `Release`，以執行更多工作。 本技術提示說明當您可能想要直接呼叫 DAO 時，MFC 協助程式可以做什麼來説明您，以及如何使用 DAO OLE 介面。 最後，此附注提供一些範例函式，示範如何直接呼叫 dao 安全性功能的 DAO。

## <a name="when-to-make-direct-dao-calls"></a>進行直接 DAO 呼叫的時機

進行直接 DAO 呼叫的最常見情況，是在需要重新整理集合時，或是當您要執行不是由 MFC 包裝的功能時。 MFC 未公開的最重要功能是安全性。 如果您想要執行安全性功能，就必須直接使用 DAO 使用者和群組物件。 除了安全性，MFC 也不支援一些其他的 DAO 功能。 其中包括記錄集複製和資料庫複寫功能，以及多個對 DAO 的延遲新增。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>簡單介紹 DAO 和 MFC 的執行

MFC 的「DAO 包裝」可讓您更輕鬆地使用 DAO，方法是處理許多細節，讓您不必擔心這一點。 這包括初始化 OLE、建立和管理 DAO 物件（特別是集合物件）、錯誤檢查，以及提供強型別、較簡單的介面（不是**VARIANT**或 `BSTR` 引數）。 您可以直接進行 DAO 呼叫，並繼續利用這些功能。 您的所有程式碼都必須針對直接 DAO 呼叫所建立的任何物件呼叫 `Release`，而*不*會修改 MFC 可能會在內部依賴的任何介面指標。 例如，除非您瞭解*所有*內部的後果，否則請勿修改開放式 `CDaoRecordset` 物件的*m_pDAORecordset*成員。 不過，您可以使用*m_pDAORecordset*介面直接呼叫 DAO 來取得 Fields 集合。 在此情況下，將不會修改*m_pDAORecordset*成員。 當您完成物件時，您只需要在 Fields 集合物件上呼叫 `Release`。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>協助簡化 DAO 呼叫的協助程式描述

提供來讓呼叫 DAO 變得更容易的協助程式，與在 MFC DAO 資料庫類別內部使用的 helper 相同。 這些協助程式是用來在進行直接的 DAO 呼叫、記錄偵錯工具輸出、檢查預期的錯誤，以及視需要擲回適當的例外狀況時，檢查傳回碼。 有兩個基礎協助程式函式和四個宏對應到這兩個 helper 的其中一個。 最佳的說明就是直接閱讀程式碼。 請參閱 AFXDAO 中的**DAO_CHECK**、 **DAO_CHECK_ERROR**、 **DAO_CHECK_MEM**和**DAO_TRACE** 。H 若要查看宏，請參閱 DAOCORE 中的**AfxDaoCheck**和**AfxDaoTrace** 。CPP.

## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 介面

DAO 物件階層中每個物件的 OLE 介面是在標頭檔 DBDAOINT 中定義。H，可以在 \Program Files\Microsoft Visual Studio .NET 2003 \ VC7\include 目錄中找到。 這些介面提供的方法可讓您操作整個 DAO 階層。

針對 DAO 介面中的許多方法，您必須操作 `BSTR` 物件（在 OLE automation 中使用長度首碼的字串）。 `BSTR` 物件通常會封裝在**VARIANT**資料類型內。 MFC 類別 `COleVariant` 本身會繼承自**VARIANT**資料類型。 根據您建立的是 ANSI 或 Unicode 專案，DAO 介面會傳回 ANSI 或 Unicode `BSTR`s。 V_BSTR 和 V_BSTRT 這兩個宏有助於確保 DAO 介面取得預期類型的 `BSTR`。

V_BSTR 將會解壓縮 `COleVariant`的*bstrVal*成員。 當您需要將 `COleVariant` 的內容傳遞至 DAO 介面的方法時，通常會使用這個宏。 下列程式碼片段會顯示使用 V_BSTR 宏的兩個 DAO DAOUser 介面方法的宣告和實際用法：

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

請注意，在上述的 `COleVariant` 函式中指定的 `VT_BSTRT` 引數，如果您要建立應用程式的 ANSI 版本和 unicode 版本的應用程式 Unicode `BSTR`，則會確保 `COleVariant` 中會有 ANSI `BSTR`。 這就是 DAO 預期的功能。

另一個宏 V_BSTRT 會根據組建類型（ANSI 或 Unicode），將 `COleVariant` 的 ANSI 或 Unicode *bstrVal*成員解壓縮。 下列程式碼示範如何將 `COleVariant` 中的 `BSTR` 值解壓縮至 `CString`中：

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

DAOVIEW 範例中會示範 V_BSTRT 宏以及其他用來開啟儲存于 `COleVariant`中之類型的技術。 具體而言，這項轉譯是在 `CCrack::strVARIANT` 方法中執行。 在可能的情況下，這個方法會將 `COleVariant` 的值轉譯成 `CString`的實例。

## <a name="simple-example-of-a-direct-call-to-dao"></a>直接呼叫 DAO 的簡單範例

當需要重新整理基礎 DAO 集合物件時，可能會發生這種情況。 一般來說，這不是必要的，但這是必要的簡單程式。 在有多個使用者建立新 tabledefs 的使用者環境中操作時，可能需要重新整理集合的範例。 在此情況下，您的 tabledefs 集合可能會過時。 若要重新整理集合，您只需要呼叫特定集合物件的 `Refresh` 方法，並檢查是否有錯誤：

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

請注意，目前所有的 DAO 集合物件介面都是 MFC DAO 資料庫類別未記載的執行詳細資料。

## <a name="using-dao-directly-for-dao-security-features"></a>直接針對 DAO 安全性功能使用 DAO

MFC DAO 資料庫類別不會包裝 DAO 安全性功能。 您必須呼叫 DAO 介面的方法，才能使用某些 DAO 安全性功能。 下列函式會設定系統資料庫，然後變更使用者的密碼。 此函式會呼叫其他三個函式，後續會定義這些函式。

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

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
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

接下來的四個範例示範如何：

- 設定系統 DAO 資料庫（。MDW 檔案）。

- 設定預設的使用者和密碼。

- 變更使用者的密碼。

- 變更的密碼。MDB 檔案。

### <a name="setting-the-system-database"></a>設定系統資料庫

以下是用來設定應用程式將使用之系統資料庫的範例函數。 在進行任何其他 DAO 呼叫之前，必須先呼叫此函式。

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>設定預設使用者和密碼

若要設定系統資料庫的預設使用者和密碼，請使用下列函數：

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>變更使用者的密碼

若要變更使用者的密碼，請使用下列函數：

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>變更的密碼。MDB 檔

變更的密碼。MDB 檔案，請使用下列函數：

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)
