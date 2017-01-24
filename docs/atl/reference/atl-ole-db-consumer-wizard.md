---
title: "ATL OLE DB 消費者精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL OLE DB 消費者精靈"
  - "ATL 專案, 加入 ATL OLE DB 消費者"
  - "連接字串 [C++], OLE DB 消費者"
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL OLE DB 消費者精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個精靈會設定 OLE DB 消費者類別，使得類別具有透過指定之 OLE DB 提供者 \(Provider\) 存取指定資料來源所需的資料繫結。  
  
> [!NOTE]
>  在 `Class` 和 \[.h 檔案\] 欄位輸入名稱之前，精靈會要求您按一下 \[**資料來源**\] 按鈕以選取資料來源。  
  
## UIElement 清單  
 **Data Source**  
 \[**資料來源**\] 按鈕讓您能夠使用指定的 OLE DB 提供者設定指定的資料來源。  當您按一下這個按鈕時，會出現 \[**資料連結內容**\] 對話方塊。  如需建立連接字串和 \[**資料連結內容**\] 對話方塊的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 文件中的[資料連結 API 概觀](https://msdn.microsoft.com/en-us/library/ms718102.aspx)。  
  
> [!NOTE]
>  在以前的版本中，按下 SHIFT 鍵再按一下 \[**資料來源**\] 按鈕，會開啟 \[開啟舊檔\] 對話方塊，讓您選取資料連結檔 \(.udl\)。  這個功能已不再支援。  
  
 對話方塊有四個索引標籤：  
  
-   \[**提供者**\] 索引標籤  
  
-   \[**連接**\] 索引標籤  
  
-   \[**進階**\] 索引標籤  
  
-   \[**全部**\] 索引標籤  
  
     下列其他資訊描述 \[**資料連結屬性**\] 對話方塊中的索引標籤。  
  
     按一下 \[**確定**\] 完成。  \[選取資料庫物件\] 對話方塊隨即出現。  從這個對話方塊選取消費者將使用的資料表、檢視或預存程序。  
  
     **提供者**  
     選取適當的提供程式來管理與資料來源的連接。  通常由所要連接之資料庫類型決定的提供者類型。  按一下 `Next` 按鈕，或按一下 \[**連線**\] 索引標籤。  
  
     **Connection**  
     此標籤的內容取決於您選擇的供應商。  雖然有很多類型的提供程式，但本章只介紹兩種最常見的提供程式的連結：SQL 和 ODBC 資料。  其他則是此處所述欄位的類似變化形式。  
  
     若為 SQL 資料：  
  
    1.  **選取或輸入伺服器名稱：**按一下下拉式清單功能表，顯示網路上所有已登錄的資料伺服器，並且選取其中一個。  
  
    2.  **輸入資訊以登入伺服器：**輸入使用者名稱和密碼以登入資料伺服器。  
  
    3.  **選取伺服器上的資料庫：** 按一下下拉式清單功能表，顯示資料伺服器上所有已登錄的資料庫，然後選取其中一個。  
  
         \-或\-  
  
         **附加資料庫檔作為資料庫名稱：**指定一個將用作資料庫的檔案；輸入明確路徑名稱。  
  
        > [!NOTE]
        >  \[資料連結屬性\] 對話方塊的 \[允許儲存密碼\] 功能會出現安全性問題。  \[輸入資訊登入伺服器\] 中有兩個選項按鈕：  
  
         **使用 Windows NT 整合式安全性**  
  
         **使用指定的使用者名稱及密碼**  
  
         如果您選取 \[使用特定使用者名稱和密碼\]，可以選擇是否儲存密碼 \(使用 \[允許儲存密碼\] 核取方塊\)，但這個選項並不安全。  建議您選取 \[**使用 Windows NT 整合安全**\]；此選項會加密密碼，因此是安全的。  
  
         您可能會遇到需要選取 \[允許儲存密碼\] 的情況。例如，如果您發行含有私用資料庫方案的程式庫，不應直接存取該資料庫，而應改用中層應用程式來驗證使用者 \(透過您選擇的任何身份驗證方案\)，然後限制使用者可用的資料排序。  
  
         若為 ODBC 資料：  
  
         1.  **指定資料來源：**您可以使用資料來源名稱或連接字串。  
  
         **使用資料來源名稱：**這個下拉式清單會顯示電腦中已註冊的資料來源。  您可以使用 [ODBC Data Source Administrator](!Alink("dasdkODBCDataSourceAdmin"))，事先設定資料來源。\- 或 \- **使用連接字串：**輸入您已取得的連接字串，或按一下 \[**建置**\] 按鈕，\[選取資料來源\] 對話方塊就會出現。  選取檔案或機器資料來源，然後按一下 \[**確定**\]。  
  
        > [!NOTE]
        >  您可以在 \[伺服器總管\] 中檢視現有連線的屬性以取得連接字串，也可以按兩下 \[伺服器總管\] 中的 \[**加入連接**\] 以建立連線。  
  
         2.  **輸入資訊以登入伺服器：**輸入使用者名稱和密碼以登入資料伺服器。  
  
         3.  請輸入要使用的初始目錄。  
  
         4.  按一下 \[**測試連接**\]，如果測試成功請按一下 \[**確定**\]。  如果不是，請檢查您的登入資訊，嘗試另一個資料庫，或者嘗試另一個資料伺服器。  
  
     **進階**  
     **網路設定：**指定 [Impersonation level](!Alink("_com_Impersonation_Levels")) \(允許伺服器在模擬用戶端時使用的模擬層級；直接對應至 RPC 模擬層級\) 和**保護層級** \(在用戶端和伺服器之間傳送之資料的保護層級；直接對應至 RPC 保護層級\)。  
  
     **其他：** 在 **連接逾時** 中，指定發生逾時之前允許的閒置時間秒數。  在**存取權限**中，指定有關資料連接的存取權限。  
  
     如需進階初始設定屬性的詳細資訊，請參閱每個特定 OLE DB 提供者所提供的文件。  
  
     **全部**  
     這個索引標籤會顯示資料來源與您所指定之連接的初始化屬性摘要。  您可以編輯這些值。  
  
     按一下 \[**確定**\] 完成。  \[選取資料庫物件\] 對話方塊隨即出現。  從這個對話方塊選取消費者將使用的資料表、檢視或預存程序。  
  
 `Class`  
 在您選取資料來源之後，這個方塊會根據您選取的資料表或預存程序 \(Stored Procedure\) 填入 \(Populate\) 預設類別名稱 \(請參閱下面的 \[選取資料來源\]\)。  您可編輯類別名稱。  
  
 **.h 檔案**  
 在您選取資料來源之後，這個方塊會根據您選取的資料表或預存程序填入預設標頭類別名稱 \(請參閱下面的 \[選取資料來源\]\)。  您可以編輯標頭檔 \(Header File\) 的名稱或選取現有的標頭檔。  
  
 **屬性化**  
 這個選項指定精靈是否要使用屬性 \(Attribute\) 或樣板宣告來建立消費者類別。  當您選取這個選項時，精靈會使用屬性而不是樣板宣告 \(這是預設選項\)。  取消選取此選項時，精靈會使用樣板宣告代替屬性。  
  
-   當您選取 \[資料表\] 做為消費者 \[**類型**\] 時，精靈便會使用 `db_source` 和 **db\_table** 屬性建立資料表及資料表存取子類別宣告，並使用 **db\_column** 建立資料行對應，例如：  
  
    ```  
    // Inject table class and table accessor class declarations  
    [  
        db_source("<initialization_string>"),  
        db_table("dbo.Orders")  
    ]  
    ...  
    // Column map  
        [ db_column(1, status=m_dwOrderIDStatus,         length=m_dwOrderIDLength) ] LONG m_OrderID;  
        [ db_column(2, status=m_dwCustomerIDStatus,         length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
        ...  
    ```  
  
     而非使用 `CTable` 樣板類別 \(Template Class\) 來宣告該資料表和資料表存取子類別，以及 BEGIN\_COLUMN\_MAP 和 END\_COLUMN\_MAP 巨集以建立該資料行對應，例如：  
  
    ```  
    // Table accessor class  
    class COrdersAccessor;  
    // Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor> >;  
    ...  
    // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor)  
        COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID,         m_dwOrderIDLength, m_dwOrderIDStatus)  
        COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID,         m_dwCustomerIDLength, m_dwCustomerIDStatus)  
        ...  
    END_COLUMN_MAP()  
    ```  
  
-   當您選取 \[命令\] 做為消費者 \[**類型**\] 時，精靈便會使用 `db_source`、**db\_command** 和 **db\_column** 屬性建立資料行對應，例如：  
  
    ```  
    [  
        db_source("<initialization_string>"),  
        db_command("SQL_command")  
    ]  
    ...  
    // Column map using db_column is the same as for consumer type of 'table'  
    ```  
  
     而非在命令類別 .h 檔案中使用命令和命令存取子類別宣告，例如：  
  
    ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor> >;  
    ...  
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as  
    // for consumer type of 'table'  
    ```  
  
 如需詳細資訊，請參閱 [Basic Mechanics of Attributes](../../windows/basic-mechanics-of-attributes.md)。  
  
 **Type**  
 選取下列任一選項按鈕來指定消費者類別是衍生自 `CTable` 或 `CCommand` \(預設\)。  
  
 **表格**  
 如果您要使用 `CTable` 或 **db\_table** 來建立資料表和資料表存取子類別宣告，請選取這個選項。  
  
 **Command**  
 如果您要使用 `CCommand` 或 **db\_command** 來建立命令和命令存取子類別宣告，請選取這個選項，  這是預設選項。  
  
 **支援**  
 選取核取方塊來指定要在消費者中支援哪種更新 \(預設為無\)。  下列每一項都會在屬性集 \(Property Set\) 對應中設定 [DBPROP\_IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715892.aspx) 和 [DBPROP\_UPDATABILITY](https://msdn.microsoft.com/en-us/library/ms722676.aspx) 的適當項目。  
  
 **變更**  
 指定消費者支援資料列集 \(Rowset\) 中的資料列資料更新。  
  
 **Insert**  
 指定消費者支援在資料列集進行資料列插入。  
  
 **Delete**  
 指定消費者支援從資料列集進行資料列刪除。  
  
## 請參閱  
 [ATL OLE DB Consumer](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [連接字串和資料連結 \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms718376.aspx)