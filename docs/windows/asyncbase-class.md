---
title: AsyncBase 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
dev_langs:
- C++
helpviewer_keywords:
- AsyncBase class
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92add8f79abd3aac7c11142fa67ea3b4bcd237d5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466198"
---
# <a name="asyncbase-class"></a>AsyncBase 類別
實作 Windows 執行階段非同步狀態機器。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename TComplete,  
   typename TProgress = Details::Nil,  
   AsyncResultType resultType = SingleResult  
>  
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;  
  
template <  
   typename TComplete,  
   AsyncResultType resultType  
>  
class AsyncBase<TComplete, Details::Nil, resultType> : public Microsoft::WRL::Implements<IAsyncInfo>;  
```  
  
#### <a name="parameters"></a>參數  
 *TComplete*  
 在非同步作業完成時，會呼叫事件處理常式。  
  
 *Tprogress>*  
 在執行中的非同步作業報告目前進度的作業時，會呼叫事件處理常式。  
  
 *resultType*  
 其中一個[AsyncResultType](../windows/asyncresulttype-enumeration.md)列舉值。 根據預設，SingleResult。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[AsyncBase::AsyncBase 建構函式](../windows/asyncbase-asyncbase-constructor.md)|初始化的執行個體**AsyncBase**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AsyncBase::Cancel 方法](../windows/asyncbase-cancel-method.md)|取消非同步作業。|  
|[AsyncBase::Close 方法](../windows/asyncbase-close-method.md)|關閉的非同步作業。|  
|[AsyncBase::FireCompletion 方法](../windows/asyncbase-firecompletion-method.md)|叫用完成事件處理常式，或重設內部進行委派。|  
|[AsyncBase::FireProgress 方法](../windows/asyncbase-fireprogress-method.md)|叫用目前的進度事件處理常式。|  
|[AsyncBase::get_ErrorCode 方法](../windows/asyncbase-get-errorcode-method.md)|擷取目前的非同步作業的錯誤碼。|  
|[AsyncBase::get_Id 方法](../windows/asyncbase-get-id-method.md)|擷取非同步作業的控制代碼。|  
|[AsyncBase::get_Status 方法](../windows/asyncbase-get-status-method.md)|擷取值，指出非同步作業的狀態。|  
|[AsyncBase::GetOnComplete 方法](../windows/asyncbase-getoncomplete-method.md)|將目前的 「 完成 」 事件處理常式的位址複製到指定的變數中。|  
|[AsyncBase::GetOnProgress 方法](../windows/asyncbase-getonprogress-method.md)|將目前的進度事件處理常式的位址複製到指定的變數中。|  
|[AsyncBase::put_Id 方法](../windows/asyncbase-put-id-method.md)|設定非同步作業的控制代碼。|  
|[AsyncBase::PutOnComplete 方法](../windows/asyncbase-putoncomplete-method.md)|指定的值設定完成事件處理常式的位址。|  
|[AsyncBase::PutOnProgress 方法](../windows/asyncbase-putonprogress-method.md)|指定的值設定進度事件處理常式的位址。|  
|[AsyncBase::Start 方法](../windows/asyncbase-start-method.md)|啟動非同步作業。|  
  
### <a name="protected-methods"></a>保護方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AsyncBase::CheckValidStateForDelegateCall 方法](../windows/asyncbase-checkvalidstatefordelegatecall-method.md)|測試是否可以修改委派屬性，在目前的非同步狀態。|  
|[AsyncBase::CheckValidStateForResultsCall 方法](../windows/asyncbase-checkvalidstateforresultscall-method.md)|測試是否可以收集在目前的非同步狀態中的非同步作業的結果。|  
|[AsyncBase::ContinueAsyncOperation 方法](../windows/asyncbase-continueasyncoperation-method.md)|判斷是否應該繼續處理非同步作業，或應該停止。|  
|[AsyncBase::CurrentStatus 方法](../windows/asyncbase-currentstatus-method.md)|擷取目前的非同步作業的狀態。|  
|[AsyncBase::ErrorCode 方法](../windows/asyncbase-errorcode-method.md)|擷取目前的非同步作業的錯誤碼。|  
|[AsyncBase::OnCancel 方法](../windows/asyncbase-oncancel-method.md)|當在衍生類別中覆寫時，取消非同步作業。|  
|[AsyncBase::OnClose 方法](../windows/asyncbase-onclose-method.md)|當在衍生類別中覆寫時，會關閉的非同步作業。|  
|[AsyncBase::OnStart 方法](../windows/asyncbase-onstart-method.md)|當在衍生類別中覆寫時，會啟動非同步作業。|  
|[AsyncBase::TryTransitionToCompleted 方法](../windows/asyncbase-trytransitiontocompleted-method.md)|表示目前的非同步作業是否已完成。|  
|[AsyncBase::TryTransitionToError 方法](../windows/asyncbase-trytransitiontoerror-method.md)|指出指定的錯誤程式碼是否可以修改的內部錯誤狀態。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `AsyncBase`  
  
 `AsyncBase`  
  
## <a name="requirements"></a>需求  
 **標頭：** async.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)