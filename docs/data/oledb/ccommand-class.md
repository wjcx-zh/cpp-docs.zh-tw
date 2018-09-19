---
title: CCommand 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
dev_langs:
- C++
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9cc04c6d9e270e0c3b5c3bd02e05b426ccf4c53
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060924"
---
# <a name="ccommand-class"></a>CCommand 類別

提供方法來設定和執行命令。  
  
## <a name="syntax"></a>語法

```cpp
template <class TAccessor = CNoAccessor,  
   template <typename T> class TRowset = CRowset,  
   class TMultiple = CNoMultipleResults>  
class CCommand :   
   public CAccessorRowset <TAccessor, TRowset>,  
   public CCommandBase,  
   public TMultiple  
```  
  
### <a name="parameters"></a>參數  

*TAccessor*<br/>
存取子類別的型別 (例如`CDynamicParameterAccessor`， `CDynamicStringAccessor`，或`CEnumeratorAccessor`) 您想要使用的命令。 預設值是`CNoAccessor`，以指定的類別不支援參數，或輸出資料行。  
  
*TRowset*<br/>
資料列集類別的型別 (例如`CArrayRowset`或`CNoRowset`) 您想要使用的命令。 預設為 `CRowset`。  
  
*TMultiple*<br/>
若要使用 OLE DB 命令可傳回多個結果，請指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)。 否則，請使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)。 如需詳細資訊，請參閱 < [IMultipleResults](/previous-versions/windows/desktop/ms721289\(v=vs.85\))。  

## <a name="requirements"></a>需求  

**標題:** atldbcli.h  
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[關閉](#close)|關閉目前的命令。|  
|[GetNextResult](#getnextresult)|使用多個結果集時，會擷取下一個結果。|  
|[開啟](#open)|執行，並選擇性地將命令繫結。|  
  
### <a name="inherited-methods"></a>繼承的方法  
  
|||  
|-|-|  
|[建立](#create)|為指定的工作階段中，建立新的命令，然後設定命令文字。|  
|[CreateCommand](#createcommand)|建立新的命令。|  
|[GetParameterInfo](#getparameterinfo)|取得命令的參數，其名稱和其類型的清單。|  
|[準備](#prepare)|驗證並最佳化目前的命令。|  
|[ReleaseCommand](#releasecommand)|釋放參數存取子，如有必要，然後再釋放命令。|  
|[SetParameterInfo](#setparameterinfo)|指定每一個命令參數的原生類型。|  
|[Unprepare](#unprepare)|捨棄目前的命令執行計畫。|  
  
## <a name="remarks"></a>備註  

當您需要執行參數為基礎的作業，或執行命令時，請使用這個類別。 如果您只需要開啟簡單的資料列集，使用[CTable](../../data/oledb/ctable-class.md)改。  
  
您使用的存取子類別會決定參數和資料繫結的方法。  
  
請注意，您無法使用預存程序使用 OLE DB Provider for Jet 因為該提供者不支援預存程序 （只允許常數中的查詢字串）。  

## <a name="close"></a> Ccommand:: Close

釋放與命令相關聯的存取子資料列集。  
  
### <a name="syntax"></a>語法

```cpp
void Close();  
```  
  
### <a name="remarks"></a>備註  

命令會使用資料列集，結果的 set 存取子，以及 （選擇性） 參數存取子 （不同於資料表，不支援參數，並不需要參數存取子）。  
  
當您執行命令時，您應該呼叫兩者`Close`並[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)之後的命令。  
  
當您想要重複執行相同的命令時，您應該藉由呼叫釋放每個結果的 set 存取子`Close`再呼叫`Execute`。 在數列的結尾，您應該釋放參數存取子，藉由呼叫`ReleaseCommand`。 另一個常見案例呼叫具有輸出參數的預存程序。 在許多提供者 （例如 SQL Server 的 OLE DB 提供者） 的輸出參數值將不會存取直到您關閉結果的 set 存取子。 呼叫`Close`關閉傳回的資料列集和結果的 set 存取子，但不是參數存取子，因此可讓您擷取輸出參數值。  
  
### <a name="example"></a>範例  

下列範例示範如何呼叫`Close`和`ReleaseCommand`當您重複執行相同的命令。  
  
[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]  
  
## <a name="getnextresult"></a> Ccommand:: Getnextresult

擷取下一個結果集，如果有的話。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected, 
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>參數  

*pulRowsAffected*<br/>
[輸入/輸出]受命令影響的資料列計數會傳回其中的記憶體指標。  
  
*bBind*<br/>
[in]指定是否自動繫結命令之後執行。 預設值是 **，則為 true**，因而導致命令來自動繫結。 設定*bBind*要**false**可防止自動繫結的命令，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者特別感興趣的）。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

如果先前擷取的結果集，此函式會釋放前一個結果集，並解除繫結資料行。 如果*bBind*是 **，則為 true**，它會繫結的新資料行。  
  
只有當您已設定來指定多個結果，您應該呼叫此函式`CCommand`樣板參數*TMultiple*=`CMultipleResults`。 

## <a name="open"></a> Ccommand:: Open

執行，並選擇性地將命令繫結。  
  
### <a name="syntax"></a>語法  
  
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

*工作階段*<br/>
[in]要在其中執行命令的工作階段。  
  
*wszCommand*<br/>
[in]若要執行，此命令傳遞 Unicode 字串。 使用時，可以是 NULL `CAccessor`，在此情況下命令將會從傳遞給的值擷取[DEFINE_COMMAND](../../data/oledb/define-command.md)巨集。 請參閱[icommand:: Execute](/previous-versions/windows/desktop/ms718095\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
*szCommand*<br/>
[in]與相同*wszCommand*不同之處在於此參數採用 ANSI 命令字串。 此方法的第四個形式可以接受 NULL 值。 本章稍後如需詳細資訊，請參閱 < 備註 >。  
  
*pPropSet*<br/>
[in]陣列的指標[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構，其中包含要設定屬性和值。 請參閱[的屬性集和屬性群組](/previous-versions/windows/desktop/ms713696\(v=vs.85\))中*OLE DB 程式設計人員參考*Windows SDK 中。  
  
*pRowsAffected*<br/>
[輸入/輸出]受命令影響的資料列計數會傳回其中的記憶體指標。 如果 *\*pRowsAffected*為 NULL，就會傳回任何資料列計數。 否則，請`Open`設定 *\*pRowsAffected*根據下列條件：  
  
|如果|然後|  
|--------|----------|  
|`cParamSets`項目`pParams`大於 1|*\*pRowsAffected*代表受到所有執行所指定的參數集的資料列總數。|  
|沒有受影響的資料列數目|*\*pRowsAffected*設定為-1。|  
|此命令不會更新、 刪除或插入資料列|*\*pRowsAffected*是未定義。|  
  
*guidCommand*<br/>
[in]剖析命令文字中指定的語法和一般的規則，若要使用的提供者 GUID。 請參閱[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\))並[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
*bBind*<br/>
[in]指定是否自動繫結命令之後執行。 預設值是 **，則為 true**，因而導致命令來自動繫結。 設定*bBind*要**false**可防止自動繫結的命令，讓您以手動方式可以繫結。 （手動繫結是 OLAP 使用者特別感興趣的）。  
  
*ulPropSets*<br/>
[in]數目[DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\))結構傳入*Dbpropset*引數。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

前三個種`Open`需要工作階段、 建立命令，並執行命令，繫結必要的任何參數。  
  
第一種形式的`Open`會採用 Unicode 命令字串，而且沒有預設值。  
  
第二個形式`Open`採用 ANSI 命令字串，並沒有 （提供與現有的 ANSI 應用程式的回溯相容性） 的預設值。  
  
第三種`Open`允許命令字串為 NULL，因為型別**int**預設值是 NULL。 它可呼叫`Open(session, NULL);`或是`Open(session);`因為 NULL 是型別**int**。這一版需要和判斷提示**int**參數為 NULL。  
  
使用的第四個形式`Open`當您已經建立命令和您想要執行單一[準備](../../data/oledb/ccommand-prepare.md)和多個執行。  
  
> [!NOTE]
>  `Open` 呼叫`Execute`，接著呼叫`GetNextResult`。 

## <a name="create"></a> Ccommand:: Create

呼叫[ccommand:: Createcommand](../../data/oledb/ccommand-createcommand.md)建立命令指定的工作階段，然後呼叫[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709825\(v=vs.85\))指定的命令文字。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::Create(const CSession& session,   
   LPCWSTR wszCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  

HRESULT CCommandBase::Create(const CSession& session,   
   LPCSTR szCommand,   
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();  
```  
  
#### <a name="parameters"></a>參數  

*工作階段*<br/>
[in]要在其中建立命令的工作階段。  
  
*wszCommand*<br/>
[in]Unicode 文字的命令字串的指標。  
  
*szCommand*<br/>
[in]ANSI 文字命令字串的指標。  
  
*guidCommand*<br/>
[in]剖析命令文字中指定的語法和一般的規則，若要使用的提供者 GUID。 如需方言的說明，請參閱 < [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

第一種形式的`Create`採用 Unicode 命令字串。 第二個形式`Create`採用 ANSI 命令字串 （提供與現有的 ANSI 應用程式的回溯相容性）。

## <a name="createcommand"></a> Ccommand:: Createcommand

建立新的命令。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();  
```  
  
#### <a name="parameters"></a>參數  

*工作階段*<br/>
[in]A`CSession`要與新的命令相關聯的物件。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

這個方法會建立使用指定的工作階段物件的命令。  

## <a name="getparameterinfo"></a> Ccommand:: Getparameterinfo

取得命令的參數，其名稱和其類型的清單。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,  
   DBPARAMINFO** ppParamInfo,  
   OLECHAR** ppNamesBuffer) throw ();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[icommandwithparameters:: Getparameterinfo](/previous-versions/windows/desktop/ms714917\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。   

## <a name="prepare"></a> Ccommand:: Prepare

驗證並最佳化目前的命令。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();  
```  
  
#### <a name="parameters"></a>參數  

*cExpectedRuns*<br/>
[in]您要執行命令的次數。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

這個方法會包裝的 OLE DB 方法[icommandprepare:: Prepare](/previous-versions/windows/desktop/ms718370\(v=vs.85\))。  

## <a name="releasecommand"></a> Ccommand:: Releasecommand

釋放參數存取子，然後再釋放命令本身。  
  
### <a name="syntax"></a>語法  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
```  
  
### <a name="remarks"></a>備註  

`ReleaseCommand` 用於搭配`Close`。 請參閱[關閉](../../data/oledb/ccommand-close.md)使用方式詳細資料。 

## <a name="setparameterinfo"></a> Ccommand:: Setparameterinfo

指定每一個命令參數的原生類型。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,  
   const DBORDINAL* pOrdinals,  
   const DBPARAMBINDINFO* pParamInfo) throw();  
```  
  
#### <a name="parameters"></a>參數  

請參閱[icommandwithparameters:: Setparameterinfo](/previous-versions/windows/desktop/ms725393\(v=vs.85\))中*OLE DB 程式設計人員參考*。  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  

## <a name="unprepare"></a> Ccommand:: Unprepare

捨棄目前的命令執行計畫。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT CCommandBase::Unprepare() throw();  
```  
  
### <a name="return-value"></a>傳回值  

標準的 HRESULT。  
  
### <a name="remarks"></a>備註  

這個方法會包裝的 OLE DB 方法[Icommandprepare](/previous-versions/windows/desktop/ms719635\(v=vs.85\))。 
  
## <a name="see-also"></a>另請參閱  

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)