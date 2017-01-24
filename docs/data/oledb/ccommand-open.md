---
title: "CCommand::Open | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CCommand.Open"
  - "ATL::CCommand::Open"
  - "CCommand.Open"
  - "CCommand::Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open 方法"
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCommand::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

執行並選擇性地將命令繫結。  
  
## 語法  
  
```  
  
      HRESULT Open(  
   const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
HRESULT Open(  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0  
) throw( );  
```  
  
#### 參數  
 `session`  
 \[in\] 是在其上執行命令的物件。  
  
 `wszCommand`  
 \[in\] 命令執行時，您可以為 Unicode 字串。  可以是 **NULL** ，使用 `CAccessor`時，在這種情況下，命令會從值會擷取傳遞至 [DEFINE\_COMMAND](../../data/oledb/define-command.md) 巨集的情況下。  請參閱《 *OLE DB 程式設計人員參考》的*[ICommand::Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) 以取得詳細資訊。  
  
 `szCommand`  
 \[in\] 和 `wszCommand` 相同，除了這個參數相同採用 ANSI 命令字串。  這個方法的第四個表單可以接受 null 值。  以後。請參閱 \< 備註 \> 主題以取得詳細資訊。  
  
 *pPropSet*  
 \[in\] 物件陣列的指標包含屬性和值的 [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構會設定。  請參閱 *《 OLE DB 程式設計人員參考》*的[屬性集合和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx) [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `pRowsAffected`  
 \[in\/out\]in\] 命令影響的計數資料行中傳回的記憶體指標。  如果 *\*pRowsAffected* 為 **NULL**，則傳回沒有資料行的數目。  否則， **Open** 會根據下列條件設定\*`pRowsAffected` :  
  
|如果|則…|  
|--------|--------|  
|`pParams` 的 **cParamSets** 項目大於 1|\*`pRowsAffected` 表示執行指定的所有受影響的資料列總數參數設定為。|  
|受影響的資料列數目是無效的|\*`pRowsAffected` 設定為 \-1。|  
|命令不會更新，而不刪除，也不會插入資料行|\*`pRowsAffected` 未定義。|  
  
 `guidCommand`  
 \[in\] 在解析指定語法和一般規則以提供者可以使用命令文字中的 GUID。  請參閱 [ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx) 和 [ICommandText::SetCommandText](https://msdn.microsoft.com/en-us/library/ms709757.aspx) *《 OLE DB 程式設計人員參考》* 的詳細資料。  
  
 `bBind`  
 \[in\] 指定是否在執行之後自動繫結至命令。  預設值為 **true**，導致命令自動繫結。  對 **false** 的設定 `bBind` 以防止命令的自動繫結，讓您可以手動繫結。\(手動繫結是特殊的感興趣 OLAP 使用者\)。  
  
 `ulPropSets`  
 \[in\] [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) 結構數目*pPropSet* 引數傳遞的。  
  
## 傳回值  
 標準版 `HRESULT`  
  
## 備註  
 **Open** 前三個表單接受會議，建立命令，以及執行命令，並視需要繫結所有參數。  
  
 **Open** 第一個表單接受 Unicode 命令字串並沒有預設值。  
  
 **Open** 第二個表單不接受 ANSI 命令字串和預設值 \(隨相容性現有 ANSI 應用程式\)。  
  
 **Open** 第三種可讓命令字串是空的，因為預設值的型別為 `int` 的空。  因為 null 屬於型別 `int`，在呼叫 `Open(session, NULL);` 或 `Open(session);` 提供。  這個版本的需求和判斷提示 `int` 參數為 null。  
  
 請使用 **Open** 第四個表單，當您已經建立訂單時，您要執行單一 [準備](../../data/oledb/ccommand-prepare.md) 和多個執行緒。  
  
> [!NOTE]
>  **Open** 呼叫 **Execute**，接著呼叫 `GetNextResult`。  
  
## 需求  
 **標題:** atldbcli.h  
  
## 請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)