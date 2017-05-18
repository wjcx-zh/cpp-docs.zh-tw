---
title: "ATL OLE DB 消費者精靈 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6e35ce9038a8fd8f7aeeb00139511a8f45c1257d
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="atl-ole-db-consumer-wizard"></a>ATL OLE DB 消費者精靈
這個精靈設定的 OLE DB 取用者類別與資料繫結到指定的 OLE DB 提供者存取指定的資料來源所需。  
  
> [!NOTE]
>  此精靈會要求您按一下**資料來源**按鈕來選取資料來源中的名稱之前，請先`Class`和**.h 檔案**欄位。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **資料來源**  
 **資料來源**按鈕可讓您設定使用指定的 OLE DB 提供者的指定的資料來源。 當您按一下這個按鈕，**資料連結屬性** 對話方塊隨即出現。 如需有關建置連接字串和**資料連結屬性**對話方塊中，請參閱[資料連結 API 概觀](https://msdn.microsoft.com/library/ms718102.aspx)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]文件。  
  
> [!NOTE]
>  在舊版中，按一下 Shift**資料來源**按鈕開啟 [開啟舊檔] 對話方塊可讓您選取的資料連結 (.udl) 檔案。 不再支援此功能。  
  
 對話方塊有四個索引標籤︰  
  
- **提供者** 索引標籤  
  
- **連接** 索引標籤  
  
- **進階** 索引標籤  
  
- **所有** 索引標籤  
  
     以下資訊描述中的索引標籤**資料連結屬性**對話方塊。  
  
     按一下 **確定**來完成。 **選取資料庫物件** 對話方塊隨即出現。 從這個對話方塊中，選取資料表、 檢視或消費者將使用的預存程序。  
  
 **提供者**  
     選取適當的提供者來管理資料來源的連接。 提供者的類型是通常取決於您所連接的資料庫的類型。 按一下  `Next`  按鈕，或按一下**連接** 索引標籤。  
  
 **連接**  
     此索引標籤的內容取決於您所選取的提供者。 雖然有許多類型的提供者，本章節內容涵蓋連接兩個最常見︰ SQL 和 ODBC 的資料。 其他則是類似的變體，此處所述的欄位。  
  
     對於 SQL 資料︰  
  
    1. **選取或輸入伺服器名稱︰**按一下以顯示所有已註冊的資料伺服器在網路上的下拉式清單功能表，然後選取其中一個。  
  
    2. **輸入要登入伺服器的資訊︰**輸入使用者名稱和密碼來登入的資料伺服器。  
  
    3. **選取的資料庫伺服器上︰**按一下下拉式清單 功能表，顯示所有已註冊的資料庫伺服器上的資料，然後選取其中一個。  
  
         -或-  
  
 **附加資料庫檔案做為資料庫名稱︰**指定要做為資料庫檔案，則輸入明確的路徑名稱。  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **使用 Windows NT 整合式安全性**  
  
 **使用特定的使用者名稱和密碼**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **使用資料來源名稱︰**這個下拉式清單會顯示在您的電腦中註冊的資料來源。 您可以設定資料來源使用 ODBC 資料來源管理員事先-或-**使用連接字串︰** ，或者輸入的連接字串，您已取得，或按一下 [**建置**按鈕;**選取資料來源**] 對話方塊隨即出現。 選取檔案或機器的資料來源，然後按一下**確定**。  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **進階**  
 **網路設定︰**指定**模擬等級**（的伺服器可以模擬用戶端時使用; 直接對應到 RPC 模擬層級的模擬層級） 和**保護層級**（層級的保護資料的用戶端和伺服器之間傳送; 直接對應到 RPC 保護層級）。  
  
 **其他︰**中**連接逾時**，指定發生逾時之前所允許的閒置時間的秒數。 在**存取權限**，指定資料連接的存取權限。  
  
     如需進階的初始化屬性的詳細資訊，請參閱每個特定的 OLE DB 提供者所隨附的文件。  
  
 **All**  
     此索引標籤會顯示您所指定的連接與資料來源的初始化內容的摘要。 您可以編輯這些值。  
  
     按一下 **確定**來完成。 **選取資料庫物件** 對話方塊隨即出現。 從這個對話方塊中，選取資料表、 檢視或消費者將使用的預存程序。  
  
 `Class`  
 選取資料來源之後，此方塊會填入基礎資料表或您所選取的預存程序的預設類別名稱 (請參閱**選取資料來源**下方)。 您可以編輯的類別名稱。  
  
 **.h 檔案**  
 選取資料來源之後，此方塊會填入基礎資料表或預存程序，您選取預設標頭類別名稱 (請參閱**選取資料來源**下方)。 您可以編輯的標頭檔的名稱，或選取現有的標頭檔。  
  
 **使用屬性**  
 此選項指定精靈是否將建立使用屬性或宣告範本的取用者類別。 當您選取此選項時，精靈會使用屬性，而不是樣板宣告 （這是預設選項）。 當您取消選取此選項時，精靈會使用樣板宣告，而非屬性。  
  
-   如果您選擇的消費者**類型**的資料表，精靈會使用`db_source`和**db_table**屬性來建立資料表和資料表的存取子類別宣告，並使用**db_column**建立資料行對應，例如︰  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     而不是使用`CTable`樣板類別宣告的資料表和資料表的存取子類別和 BEGIN_COLUMN_MAP 和 END_COLUMN_MAP 巨集，以建立資料行對應，例如︰  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   如果您選擇的消費者**類型**的命令，精靈會使用`db_source`和**db_command**屬性，並使用**db_column**建立資料行對應，例如︰  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     而不是使用命令和命令存取子類別宣告中的命令類別.h 檔案中，例如︰  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 請參閱[屬性的基本機制](../../windows/basic-mechanics-of-attributes.md)如需詳細資訊。  
  
 **Type**  
 選取其中一個選項按鈕來指定是否將取用者類別衍生自`CTable`或`CCommand`（預設值）。  
  
 **資料表**  
 選取此選項，如果您想要使用`CTable`或**db_table**來建立資料表和資料表的存取子類別宣告。  
  
 **命令**  
 選取此選項，如果您想要使用`CCommand`或**db_command**建立命令和命令存取子類別宣告。 這是預設選取項目。  
  
 **支援**  
 選取核取方塊，以指定的取用者 （預設為無） 支援的更新類型。 在下列各將[DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx)和適當的項目，如[DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx)屬性中設定對應。  
  
 **變更**  
 指定取用者支援更新資料列資料的資料列集。  
  
 **插入**  
 指定消費者支援插入資料列集的資料列。  
  
 **刪除**  
 指定取用者支援的資料列集資料列的刪除。  
  
## <a name="see-also"></a>另請參閱  
 [ATL OLE DB 消費者](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [連接字串和資料連結 (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)

