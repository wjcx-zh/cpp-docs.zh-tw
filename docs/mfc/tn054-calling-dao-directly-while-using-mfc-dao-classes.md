---
title: TN054： 使用 MFC DAO 類別時直接呼叫 DAO |Microsoft 文件
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.dao
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f060364a8c08a32acae49a0386911486251b0e31
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122447"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054：在使用 MFC DAO 類別時直接呼叫 DAO

> [!NOTE]
> Visual c + + 環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 呤魽您畷樾[OLE DB 樣板](../data/oledb/ole-db-templates.md)或[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO 中維護現有應用程式。

當使用 MFC DAO 資料庫類別，則可能是直接使用 DAO 所需的情況。 通常，這是大小寫，但 MFC 提供一些 helper 機制，以便讓直接 DAO 呼叫簡單直接的 DAO 呼叫合併使用 MFC 類別時。 進行直接 DAO MFC managed DAO 物件方法的呼叫應該需要只需幾行程式碼。 如果您需要建立及使用的 DAO 物件*不*由 MFC 進行管理，您必須執行更多的工作實際呼叫`Release`物件上。 這個技術提示說明當您可能想要直接呼叫 DAO、 MFC helper 可以執行可協助您，以及如何使用 DAO OLE 介面。 最後，這個提示會提供顯示如何 DAO 安全性功能的直接呼叫 DAO 某些範例函式。

## <a name="when-to-make-direct-dao-calls"></a>當進行直接 DAO 呼叫

當需要重新整理的集合時，就會發生最常見的情況下進行直接呼叫 DAO 或當您實作功能不會由 MFC 包裝。 MFC 未公開的最重要功能是安全性。 如果您想要實作安全性功能，您必須直接使用的 DAO 的使用者和群組物件。 安全性，除了有只有少數 DAO 不支援的其他功能 MFC。 這些包括資料錄集的複製和資料庫複寫的功能，以及 dao 少數晚期新增項目。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>簡要概述 DAO 和 MFC 的實作

MFC 的文繞圖的 DAO 會使得使用 DAO 的簡單，藉由處理許多細節，因此您不需要擔心的一些事項。 這包括 OLE、 建立和管理的 DAO 物件 （尤其是集合物件），錯誤檢查，以及提供強型別、 更簡單的介面初始化 (沒有**VARIANT**或`BSTR`引數）。 您可以直接 DAO 呼叫，同時仍然利用這些功能。 您的程式碼必須執行的就是呼叫`Release`直接 DAO 所建立的任何物件的呼叫和*不*修改任何 MFC 依賴內部的介面指標。 例如，請勿修改*m_pDAORecordset*隸屬開啟`CDaoRecordset`物件，除非您了解*所有*內部的後果。 不過，您可以使用*m_pDAORecordset*介面呼叫 DAO 直接取得的欄位集合。 在此情況下*m_pDAORecordset*成員將不會修改。 您只需要呼叫`Release`上的欄位集合物件與物件完成時。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>會呼叫更容易進行 DAO 的協助程式的描述

提供給進行呼叫 DAO 的簡單的 helper 是 MFC DAO 資料庫類別的內部使用的相同 helper。 這些協助程式用來檢查傳回碼，當進行直接的 DAO 呼叫，檢查預期的錯誤，並擲回適當的例外狀況，必要時，記錄偵錯輸出。 有兩個基礎的 helper 函式和四個巨集對應至其中一個這些兩個協助程式。 最佳的說明，可直接閱讀的程式碼。 請參閱**DAO_CHECK**， **DAO_CHECK_ERROR**， **DAO_CHECK_MEM**，和**DAO_TRACE** AFXDAO 中。H 看到巨集，並且看到**AfxDaoCheck**和**AfxDaoTrace** DAOCORE 中。CPP。

## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 介面

標頭檔 DBDAOINT 中定義的 OLE 介面，DAO 物件階層中每個物件。H、 \Program Files\Microsoft Visual Studio.NET 2003\VC7\include 目錄中找到。 這些介面會提供方法，可讓您管理整個 DAO 階層。

許多 DAO 介面中的方法，您將需要管理`BSTR`物件 （固定長度字串 OLE automation 中使用）。 `BSTR`物件通常封裝在**VARIANT**資料型別。 MFC 類別`COleVariant`本身可以繼承自**VARIANT**資料型別。 根據是否為 ANSI 或 Unicode 建置專案，DAO 介面會傳回 ANSI 或 Unicode `BSTR`s。 兩個巨集，V_BSTR 和 V_BSTRT，很有用，為確保 DAO 介面取得`BSTR`是預期的類型。

將會擷取 V_BSTR *bstrVal*隸屬`COleVariant`。 如果您要傳遞的內容，通常使用此巨集`COleVariant`DAO 介面的方法。 下列程式碼片段顯示的宣告 」 和 「 實際使用的 DAO DAOUser 介面充分利用 V_BSTR 巨集的兩個方法：

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted
DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;

DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

請注意，`VT_BSTRT`引數中指定`COleVariant`上述建構函式可確保會使用 ANSI`BSTR`中`COleVariant`如果您建置應用程式和 Unicode ANSI 版本`BSTR`的 Unicode 版本您的應用程式。 這是 DAO 所預期的內容。

其他巨集，V_BSTRT，將會擷取 ANSI 或 Unicode *bstrVal*隸屬`COleVariant`根據組建 （ANSI 或 Unicode） 的類型。 下列程式碼示範如何擷取`BSTR`值`COleVariant`到`CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

V_BSTRT 巨集，以及其他技術來開啟儲存在其他類型`COleVariant`，DAOVIEW 範例所示。 具體來說，會在中執行這項轉譯`CCrack::strVARIANT`方法。 這個方法，如果可行，會轉譯的值`COleVariant`的執行個體`CString`。

## <a name="simple-example-of-a-direct-call-to-dao"></a>直接呼叫 DAO 的簡單範例

需要重新整理基礎 DAO 集合物件時，可能會發生的情況。 一般來說，這不能有必要，但它是簡單的程序，如果有必要。 舉例來說，當集合可能需要重新整理時，多個使用者建立新的 tabledefs 多使用者環境中運作。 在此情況下 tabledefs 集合可能會變成過時。 若要重新整理的集合，您只需要呼叫`Refresh`特定集合的物件並檢查是否有錯誤的方法：

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

請注意，目前所有的 DAO 集合物件介面 MFC DAO 資料庫類別中未記載的實作詳細資料。

## <a name="using-dao-directly-for-dao-security-features"></a>DAO 安全性功能的直接使用 DAO

MFC DAO 資料庫類別不會換行 DAO 安全性功能。 您必須呼叫方法的 DAO 介面，以使用 DAO 的安全性功能。 下列函式設定的系統資料庫，然後變更 使用者的密碼。 此函式呼叫三個其他函式，接著定義。

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

接下來四個範例將示範如何：

- 設定系統 DAO 資料庫 (。MDW 檔案）。

- 設定預設使用者名稱和密碼。

- 變更使用者的密碼。

- 變更的密碼。MDB 檔。

### <a name="setting-the-system-database"></a>設定系統資料庫

以下是範例函式來設定將應用程式所使用的系統資料庫。 進行任何其他 DAO 呼叫之前，必須呼叫此函式。

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

### <a name="setting-the-default-user-and-password"></a>設定預設使用者名稱和密碼

若要設定的預設使用者和系統資料庫的密碼，請使用下列函數：

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

### <a name="changing-the-password-of-an-mdb-file"></a>密碼的變更。MDB 檔

若要變更的密碼。MDB 檔案，請使用下列函數：

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

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)  
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)  
