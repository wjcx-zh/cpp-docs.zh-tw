---
title: TN054:在使用 MFC DAO 類別時直接呼叫 DAO
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dao
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
ms.openlocfilehash: 938381f55b598911b69bb25bf7af576dfdfb2e4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399651"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054:在使用 MFC DAO 類別時直接呼叫 DAO

> [!NOTE]
> 視覺效果C++環境和精靈不支援 DAO （雖然 DAO 類別都包含在內，而且您仍然可以使用它們）。 Microsoft 建議您改用[OLE DB 樣板](../data/oledb/ole-db-templates.md)或是[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)針對新的專案。 您只應該使用 DAO，在維護現有的應用程式。

使用 MFC DAO 資料庫類別時，可能會有一些情況需要直接使用 DAO。 通常，這不是如此，但 MFC 提供了一些協助程式機制，以協助進行直接 DAO 呼叫簡單，當合併使用 「 MFC 類別與 DAO 的直接呼叫。 進行直接的 DAO MFC managed 的 DAO 物件之方法的呼叫應該要求只需幾行程式碼。 如果您需要建立和使用的 DAO 物件*未*MFC 所管理，您必須做多一點的工作實際呼叫`Release`物件上。 這個技術提示說明當您可能想要直接呼叫 DAO、 MFC 協助程式功能可協助您，以及如何使用 DAO OLE 介面。 最後，這個附註會提供示範如何針對 DAO 安全性功能的直接呼叫 DAO 某些範例函式。

## <a name="when-to-make-direct-dao-calls"></a>當進行直接的 DAO 呼叫

當集合需要重新整理時，就會發生最常見的情況下進行直接呼叫 DAO 或當您實作不會由 MFC 包裝的功能。 最重要的功能不會公開由 MFC 是安全性。 如果您想要實作安全性功能，您必須直接使用的 DAO 使用者和群組物件。 除了安全性有只有少數 DAO 不支援的其他功能 MFC。 這些包括資料錄集的複製和資料庫複寫的功能，以及少數 dao 晚期的增補。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO 和 MFC 的實作的簡短概觀

使用的 DAO 更容易藉由處理許多詳細資料，因此您不需要擔心微不足道的 DAO 讓 MFC 的換行。 這包括初始化 OLE、 建立和管理的 DAO 物件 （特別是集合物件），錯誤檢查，並提供強型別、 更簡單的介面 (沒有**VARIANT**或`BSTR`引數）。 您可以進行直接的 DAO 呼叫，同時仍然利用這些功能。 您的程式碼必須做的是呼叫`Release`直接 DAO 所建立的任何物件的呼叫並*不*修改任何 MFC 可能會在內部仰賴的介面指標。 比方說，不會修改*m_pDAORecordset*屬於開放`CDaoRecordset`物件，除非您了解*所有*內部的後果。 不過，您可以使用*m_pDAORecordset*介面呼叫 DAO，直接以取得欄位集合。 在此情況下*m_pDAORecordset*成員將不會修改。 您只需要呼叫`Release`與物件完成時，才會進行欄位集合物件。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>描述讓 DAO 的協助程式會呼叫您更輕鬆

可讓呼叫 DAO 的簡單的協助程式是 MFC DAO 資料庫類別的內部使用的相同協助程式。 這些協助程式用來檢查傳回碼，當進行直接的 DAO 呼叫，檢查預期的錯誤，並擲回適當的例外狀況，必要時，記錄偵錯輸出。 有兩個基礎的 helper 函式和四個巨集對應至其中一個這些兩個協助程式。 只需讀取的程式碼是最佳的說明。 請參閱**DAO_CHECK**， **DAO_CHECK_ERROR**， **DAO_CHECK_MEM**，以及**DAO_TRACE** AFXDAO 中。H，以查看巨集，以及查看**AfxDaoCheck**並**AfxDaoTrace** DAOCORE 中。CPP。

## <a name="using-the-dao-ole-interfaces"></a>使用 DAO OLE 介面

DAO 物件階層中每個物件的 OLE 介面被定義在標頭檔 DBDAOINT。H、 \Program Files\Microsoft Visual Studio.NET 2003\VC7\include 目錄中找到。 這些介面會提供方法，可讓您管理整個階層中，DAO。

許多 DAO 介面中的方法，您必須操作`BSTR`物件 （長度前置字串 OLE automation 中使用）。 `BSTR`物件通常會封裝內**VARIANT**資料型別。 MFC 類別`COleVariant`本身是繼承自**VARIANT**資料型別。 根據是否您建置專案時的 ANSI 或 Unicode，ANSI 或 Unicode，會傳回 DAO 介面`BSTR`s。 兩個巨集，V_BSTR 和 V_BSTRT，適合，為確保 DAO 介面取得`BSTR`是預期的類型。

會擷取 V_BSTR *bstrVal*隸屬`COleVariant`。 當您需要傳遞的內容時，通常使用此巨集`COleVariant`DAO 介面的方法。 下列程式碼片段顯示的宣告 」 和 「 實際使用的 DAO DAOUser 介面善用 V_BSTR 巨集的兩個方法：

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

請注意，`VT_BSTRT`中指定的引數`COleVariant`上述建構函式可確保會為 ANSI`BSTR`中`COleVariant`如果您建置您的應用程式和 Unicode 的 ANSI 版本`BSTR`的 Unicode 版本您的應用程式。 這是 DAO 所預期的內容。

其他巨集，V_BSTRT，就會擷取 ANSI 或 Unicode *bstrVal*隸屬`COleVariant`根據的組建 （ANSI 或 Unicode） 型別。 下列程式碼示範如何擷取`BSTR`值從`COleVariant`到`CString`:

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

V_BSTRT 巨集，以及其他技術來開啟儲存在其他類型`COleVariant`，DAOVIEW 範例所示。 具體來說，在中執行這項轉譯`CCrack::strVARIANT`方法。 這個方法，可能的話，會轉譯的值`COleVariant`的執行個體`CString`。

## <a name="simple-example-of-a-direct-call-to-dao"></a>直接呼叫 DAO 的簡單範例

需要重新整理基礎 DAO 集合物件時，可能會發生的情況。 一般來說，這不能有必要，但是它是簡單的程序，如有必要。 舉例來說，當集合可能需要重新整理時，在多使用者環境下作業的多個使用者建立新的 tabledefs。 在此情況下 tabledefs 集合可能會變成過時。 若要重新整理的集合，您只需要呼叫`Refresh`特定的集合物件並檢查是否有錯誤的方法：

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

請注意，目前所有的 DAO 集合物件介面的 MFC DAO 資料庫類別的未記載的實作詳細資料。

## <a name="using-dao-directly-for-dao-security-features"></a>使用 DAO 直接 DAO 安全性功能

MFC DAO 資料庫類別不會換行 DAO 安全性功能。 您必須呼叫 DAO 介面，以便使用 DAO 的安全性功能的方法。 下列函式會設定系統資料庫，然後變更 使用者的密碼。 此函式呼叫三個其他函式，接著定義。

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

- 變更的密碼。MDB 檔案。

### <a name="setting-the-system-database"></a>設定系統資料庫

以下是範例函式，若要設定將由應用程式的系統資料庫。 進行任何其他的 DAO 呼叫之前，必須呼叫此函式。

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

若要設定的預設使用者和系統資料庫的密碼，請使用下列函式：

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

若要變更使用者的密碼，請使用下列函式：

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

若要變更的密碼。MDB 檔案，請使用下列函式：

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
