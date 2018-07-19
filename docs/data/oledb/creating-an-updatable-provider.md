---
title: 建立可更新的提供者 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbcd69168b70e8d85bf2b90c3f456f79cd1c228c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38954580"
---
# <a name="creating-an-updatable-provider"></a>建立可更新的提供者

Visual c + + 支援可更新的提供者 」 或 「 可更新的提供者 （寫入） 資料存放區。 本主題討論如何建立可更新的提供者使用 OLE DB 範本。  
  
 本主題假設您要啟動的可運作的提供者。 有兩個步驟來建立可更新的提供者。 您必須先決定要如何提供者時，將資料存放區中，進行變更具體而言，變更會立即進行還是延後，直到發出 update 命令。 一節 「[讓提供者可更新](#vchowmakingprovidersupdatable)」 描述的變更與您只需要提供者程式碼中的設定。  
  
 接下來，您必須確定您的提供者包含所有的功能來支援取用者可能會要求它的任何項目。 如果取用者想要更新資料存放區，提供者必須包含資料保存到資料存放區的程式碼。 比方說，您可能會使用 MFC 的 C 執行階段程式庫來執行這類作業在資料來源。 一節 「[寫入至資料來源](#vchowwritingtothedatasource)」 說明如何寫入至資料來源、 處理`NULL`和預設值，以及設定資料行的旗標。  
  
> [!NOTE]
>  UpdatePV 是可更新的提供者的範例。 為 MyProv，但具有可更新的支援 UpdatePV 都是一樣的。  
  
##  <a name="vchowmakingprovidersupdatable"></a> 建立可更新的提供者  

 若要讓提供者可更新的索引鍵了解您想要您的提供者，在資料存放區和如何在您想要執行這些作業的提供者上執行哪些的作業。 具體而言，主要問題是是否要立即或延後更新資料存放區 （批次處理） 直到發出 update 命令。  
  
 您必須先決定是否要繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`在您的資料列集類別。 根據這些您的選擇來實作，將會受到影響的三種方法的功能： `SetData`， `InsertRows`，和`DeleteRows`。  
  
- 如果您繼承自[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)，立即呼叫這三種方法會變更資料存放區。  
  
- 如果您繼承自[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)，方法會延遲到資料存放區的變更，直到您呼叫`Update`， `GetOriginalData`，或`Undo`。 如果更新涉及數項變更，他們會執行批次模式 （請注意，批次的變更可以加入大量的記憶體額外負荷）。  
  
 請注意，`IRowsetUpdateImpl`衍生自`IRowsetChangeImpl`。 因此，`IRowsetUpdateImpl`可讓您變更功能，以及批次功能。  
  
#### <a name="to-support-updatability-in-your-provider"></a>若要在您的提供者支援更新的能力  
  
1. 在您的資料列集類別，繼承自`IRowsetChangeImpl`或`IRowsetUpdateImpl`。 這些類別會提供適當的介面，來變更資料存放區：  
  
     **新增 IRowsetChange**  
  
     新增`IRowsetChangeImpl`您使用這種形式的繼承鏈結：  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     也加入`COM_INTERFACE_ENTRY(IRowsetChange)`至`BEGIN_COM_MAP`資料列集類別中的區段。  
  
     **新增 IRowsetUpdate**  
  
     新增`IRowsetUpdate`您使用這種形式的繼承鏈結：  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  您應該移除`IRowsetChangeImpl`繼承鏈結中的一行。 此一的例外狀況，以先前所述的指示詞必須包含的程式碼`IRowsetChangeImpl`。  
  
2.  將下列內容新增至 COM 對應 (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |如果您實作|將新增到 COM 對應|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  在命令中，將下列內容新增至您的屬性集對應 (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |如果您實作|將加入至屬性集合對應|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  在屬性集對應，您應該也包含下列設定的所有下面所列：  
  
    ```  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     您可以找到這些巨集呼叫中使用，藉由尋找為 Atldb.h 中的屬性識別碼和值的值 （如果為 Atldb.h 和不同的線上文件，為 Atldb.h 取代文件）。  
  
    > [!NOTE]
    >  許多`VARIANT_FALSE`和`VARIANT_TRUE`設定所需的 OLE DB 範本; OLE DB 規格表示它們可以是讀取/寫入，但 OLE DB 範本只能支援一個值。  
  
     **如果您實作 IRowsetChangeImpl**  
  
     如果您實作`IRowsetChangeImpl`，您必須在您的提供者上設定下列屬性。 這些屬性主要用來要求介面傳遞`ICommandProperties::SetProperties`。  
  
    - `DBPROP_IRowsetChange`： 設定就會自動設定`DBPROP_IRowsetChange`。  
  
    - `DBPROP_UPDATABILITY`： 指定支援的方法位元遮罩`IRowsetChange`: `SetData`， `DeleteRows`，或`InsertRow`。  
  
    - `DBPROP_CHANGEINSERTEDROWS`： 取用者可以呼叫`IRowsetChange::DeleteRows`或`SetData`新插入的資料列。  
  
    - `DBPROP_IMMOBILEROWS`： 資料列集不會重新排列插入或更新的資料列。  
  
     **如果您實作 IRowsetUpdateImpl**  
  
     如果您實作`IRowsetUpdateImpl`，您必須設定下列屬性在您的提供者，另外設定的所有屬性`IRowsetChangeImpl`先前所列：  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OWNUPDATEDELETE`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OTHERINSERT`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_OTHERUPDATEDELETE`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_REMOVEDELETED`： 必須是 READ_ONLY 和為 VARIANT_TRUE。  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  如果您支援通知，您可能還有其他一些屬性以及;請參閱節`IRowsetNotifyCP`如這份清單。  
  
##  <a name="vchowwritingtothedatasource"></a> 寫入至資料來源  
 若要讀取的資料來源，請呼叫`Execute`函式。 若要寫入的資料來源，請呼叫`FlushData`函式。 （在一般狀況下，排清方法來儲存您對資料表或索引到磁碟進行的修改）。  

