---
title: "Ccommand:: Open |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: 4c9b8f31-faf3-452d-9a29-3d3e5f54d6f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf4d30382224cd1fe85d12623acdcb90b0dee1bd
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandopen"></a>CCommand::Open
執行，並選擇性地將命令繫結。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(const CSession& session,  
   LPCWSTR wszCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   LPCSTR szCommand,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(const CSession& session,  
   INT szCommand = NULL,  
   DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   REFGUID guidCommand = DBGUID_DEFAULT,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  


HRESULT Open(DBPROPSET *pPropSet = NULL,  
   DBROWCOUNT* pRowsAffected = NULL,  
   bool bBind = true,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  
 `session`  
 [in]要在其中執行命令工作階段。  
  
 `wszCommand`  
 [in]若要執行，此命令傳遞的 Unicode 字串。 可以是**NULL**時使用`CAccessor`，在此情況下命令將會從傳遞給的值擷取[DEFINE_COMMAND](../../data/oledb/define-command.md)巨集。 請參閱[icommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx)中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
 `szCommand`  
 [in]與相同`wszCommand`不同之處在於此參數採用的 ANSI 命令字串。 這個方法的第四個形式可接受 NULL 值。 本文稍後如需詳細資訊，請參閱 < 備註 >。  
  
 *pPropSet*  
 [in]陣列的指標[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構，其中包含要設定屬性和值。 請參閱[屬性集和屬性群組](https://msdn.microsoft.com/en-us/library/ms713696.aspx)中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
 `pRowsAffected`  
 [輸入/輸出]其中會傳回命令影響的資料列計數的記憶體指標。 如果 *\*pRowsAffected*是**NULL**，會傳回任何資料列計數。 否則，**開啟**設定 *`pRowsAffected`根據下列條件：  
  
|如果|然後|  
|--------|----------|  
|**CParamSets**元素`pParams`大於 1|*`pRowsAffected` 表示受到執行所指定的參數集的所有資料列的總數。|  
|不受影響的資料列的編號|*`pRowsAffected` 設定為-1。|  
|此命令不會更新、 刪除或插入資料列|*`pRowsAffected` 未定義。|  
  
 `guidCommand`  
 [in]剖析命令文字中指定的語法和一般的規則，若要使用的提供者的 GUID。 請參閱[ICommandText::GetCommandText](https://msdn.microsoft.com/en-us/library/ms709825.aspx)和[icommandtext:: Setcommandtext](https://msdn.microsoft.com/en-us/library/ms709757.aspx)中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
 `bBind`  
 [in]指定是否要自動繫結的命令之後執行。 預設值是**true**，因而導致命令會自動繫結。 設定`bBind`至**false**可防止自動繫結的命令，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者的特別感興趣的）。  
  
 `ulPropSets`  
 [in]數目[DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)結構傳入*Dbpropset*引數。  
  
## <a name="return-value"></a>傳回值  
 標準 `HRESULT`。  
  
## <a name="remarks"></a>備註  
 第一次三種形式**開啟**需要工作階段、 建立命令，並執行命令，視繫結任何參數。  
  
 第一種形式的**開啟**會採用 Unicode 命令字串，而且沒有預設值。  
  
 第二種**開啟**接受 ANSI 命令字串，而沒有預設值 （提供與現有的 ANSI 應用程式的回溯相容性）。  
  
 第三種**開啟**允許為 NULL，因為類型的命令字串`int`預設值是 NULL。 提供用於呼叫`Open(session, NULL);`或`Open(session);`因為 NULL 是型別`int`。 這個版本需要和判斷提示，`int`參數可以是 NULL。  
  
 使用的第四個形式**開啟**當您已經建立命令，而且您想要執行單一[準備](../../data/oledb/ccommand-prepare.md)和多次執行。  
  
> [!NOTE]
>  **開啟**呼叫**Execute**，接著呼叫`GetNextResult`。  
  
## <a name="requirements"></a>需求  
 **標題:** atldbcli.h  
  
## <a name="see-also"></a>請參閱  
 [CCommand 類別](../../data/oledb/ccommand-class.md)