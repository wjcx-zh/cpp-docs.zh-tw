---
title: IVirtualProcessorRoot 結構
ms.date: 11/04/2016
f1_keywords:
- IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Activate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::Deactivate
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::EnsureAllTasksVisible
- CONCRTRM/concurrency::IVirtualProcessorRoot::IVirtualProcessorRoot::GetId
helpviewer_keywords:
- IVirtualProcessorRoot structure
ms.assetid: 5ef371b8-9e4f-4fef-bb0d-49099693dd2b
ms.openlocfilehash: f642a29d0a80568f7a5f2a5e89f6951d4819243e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364252"
---
# <a name="ivirtualprocessorroot-structure"></a>IVirtualProcessorRoot 結構

執行緒 Proxy 可以在其上執行的硬體執行緒的抽象概念。

## <a name="syntax"></a>語法

```cpp
struct IVirtualProcessorRoot : public IExecutionResource;
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[I虛擬處理器根:啟動](#activate)|使與執行上下文介面`pContext`關聯的線程代理開始在此虛擬處理器根上執行。|
|[I虛擬處理器根::D啟動](#deactivate)|導致當前在此虛擬處理器根上執行的線程代理停止調度執行上下文。 線程代理將在調用`Activate`方法時繼續執行。|
|[I虛擬處理器根::確保所有任務可見](#ensurealltasksvisible)|使存儲在各個處理器的記憶體層次結構中的數據對系統上的所有處理器都可見。 它可確保在方法返回之前在所有處理器上執行完整的記憶體圍欄。|
|[I虛擬處理器根:GetId](#getid)|返回虛擬處理器根的唯一標識符。|

## <a name="remarks"></a>備註

每個虛擬處理器根都有關聯的執行資源。 介面`IVirtualProcessorRoot`從[I執行資源](iexecutionresource-structure.md)介面繼承。 多個虛擬處理器根可能對應於同一基礎硬體線程。

資源管理員將虛擬處理器根授予計劃程式以回應資源請求。 計劃程式可以使用虛擬處理器根通過使用執行上下文啟動它來執行工作。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[I 執行資源](iexecutionresource-structure.md)

`IVirtualProcessorRoot`

## <a name="requirements"></a>需求

**標題:** concrtrm.h

**命名空間:** 併發

## <a name="ivirtualprocessorrootactivate-method"></a><a name="activate"></a>I虛擬處理器根:啟動方法

使與執行上下文介面`pContext`關聯的線程代理開始在此虛擬處理器根上執行。

```cpp
virtual void Activate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
將在此虛擬處理器根上調度的執行上下文的介面。

### <a name="remarks"></a>備註

如果線程代理未與執行上下文介面關聯,資源管理員將提供線程代理`pContext`

該方法`Activate`可用於開始執行資源管理器返回的新虛擬處理器根的工作,或恢復已停用或即將停用的虛擬處理器根上的線程代理。 有關停用的詳細資訊,請參閱[IVirtualProcessorRoot::D啟動](#deactivate)。 恢復停用的虛擬處理器根時,參數`pContext`必須與用於停用虛擬處理器根的參數相同。

首次啟動虛擬處理器根后,後續對調用`Deactivate``Activate`可能會相互競爭。 這意味著資源管理器在收到其應為的`Activate``Deactivate`呼叫之前可以收到呼叫。

啟動虛擬處理器根時,會向資源管理器發出信號,表明此虛擬處理器根當前正忙於工作。 如果計劃程式找不到在此根上執行的任何工作,則應呼叫方法,`Deactivate`通知資源管理器虛擬處理器根處於空閒狀態。 資源管理器使用此數據來負載平衡系統。

`invalid_argument`如果參數`pContext`有`NULL`值 ,則引發 。

`invalid_operation`如果參數`pContext`不表示此虛擬處理器根最近調度的執行上下文,則引發該參數。

啟動虛擬處理器根的行為將基礎硬體線程的訂閱級別增加一個。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootdeactivate-method"></a><a name="deactivate"></a>I虛擬處理器Root::D啟動方法

導致當前在此虛擬處理器根上執行的線程代理停止調度執行上下文。 線程代理將在調用`Activate`方法時繼續執行。

```cpp
virtual bool Deactivate(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
當前由此根調度的上下文。

### <a name="return-value"></a>傳回值

布林值。 **值 true**表示線程`Deactivate`代理從 方法返回以回應`Activate`對方法的 調用。 的值`false`指示線程代理從 方法返回以回應資源管理器中的通知事件。 在使用者模式可分排 (UMS) 執行緒計畫程式上,這表示專案已出現在計畫程式的完成清單中,並且計劃程式需要處理它們。

### <a name="remarks"></a>備註

當在計劃程式中找不到任何工作時,使用此方法可以暫時停止執行虛擬處理器根。 對方法的`Deactivate`調用必須源自上次啟動虛擬處理器`Dispatch`根的執行上下文的方法。 換句話說,調用該方法的`Deactivate`線程代理必須是當前在虛擬處理器根上執行的代理。 在未執行的虛擬處理器根上調用方法可能會導致未定義的行為。

停用的虛擬處理器根可能透過呼叫方法喚醒,`Activate`其參數與傳遞`Deactivate`給 該方法的參數相同。 計劃程序負責確保對`Activate`和`Deactivate`方法的調用是配對的,但不需要按特定順序接收它們。 資源管理員可以在收到對`Activate`該方法的調用之前處理對該方法的調用`Deactivate`。

如果虛擬處理器根喚醒`Deactivate`,並且方法的返回值為**false**值,則計劃`IUMSCompletionList::GetUnblockNotifications`程式應通過 該方法查詢 UMS 完成清單,對該資訊執行`Deactivate`操作,然後再次調用 該方法。 應重複這一點,`Deactivate`直到方法返回`true`值 為止。

`invalid_argument`如果參數的值為`pContext`NULL,則引發該參數。

`invalid_operation`如果虛擬處理器根從未啟動,或者參數`pContext`不表示此虛擬處理器根最近調度的執行上下文,則引發該參數。

停用虛擬處理器根的行為將基礎硬體線程的訂閱級別降低一個。 有關訂閱等級的詳細資訊,請參閱[I 執行資源::當前訂閱等級](iexecutionresource-structure.md#currentsubscriptionlevel)。

## <a name="ivirtualprocessorrootensurealltasksvisible-method"></a><a name="ensurealltasksvisible"></a>I虛擬處理器根::確保所有任務可見方法

使存儲在各個處理器的記憶體層次結構中的數據對系統上的所有處理器都可見。 它可確保在方法返回之前在所有處理器上執行完整的記憶體圍欄。

```cpp
virtual void EnsureAllTasksVisible(_Inout_ IExecutionContext* pContext) = 0;
```

### <a name="parameters"></a>參數

*pContext*<br/>
當前由此虛擬處理器根調度的上下文。

### <a name="remarks"></a>備註

當您要同步虛擬處理器根的停用以及向計畫程式添加新工作時,您可能會發現此方法很有用。 出於性能原因,您可能決定在不執行記憶體障礙的情況下將工作項添加到計劃程式,這意味著在一個處理器上執行的線程添加的工作項對所有其他處理器都無法立即看到。 通過將此方法與`Deactivate`方法結合使用,可以確保計劃程式不會在計劃程式集合中存在工作項時停用其所有虛擬處理器根。

對方法的`EnsureAllTasksVisibleThe`調用必須源自上次啟動虛擬處理器`Dispatch`根的執行上下文的方法。 換句話說,調用該方法的`EnsureAllTasksVisible`線程代理必須是當前在虛擬處理器根上執行的代理。 在未執行的虛擬處理器根上調用方法可能會導致未定義的行為。

`invalid_argument`如果參數`pContext`有`NULL`值 ,則引發 。

`invalid_operation`如果虛擬處理器根從未啟動,或者參數`pContext`不表示此虛擬處理器根最近調度的執行上下文,則引發該參數。

## <a name="ivirtualprocessorrootgetid-method"></a><a name="getid"></a>I虛擬處理器根:GetId 方法

返回虛擬處理器根的唯一標識符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>傳回值

整數標識碼。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
