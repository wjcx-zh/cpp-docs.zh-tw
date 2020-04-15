---
title: 工人原型
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: b0b32232d7386df0c0f13a1c3af1003369b906e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329339"
---
# <a name="worker-archetype"></a>工人原型

符合*輔助角色*原型的類提供處理線程池上排隊的工作項的代碼。

**實作**

要實現符合此原型的類,類必須提供以下功能:

|方法|描述|
|------------|-----------------|
|[[初始化]](#initialize)|調用 以在將任何請求傳遞到[執行](#execute)之前初始化輔助角色物件。|
|[執行](#execute)|調用以處理工作項。|
|[終止](#terminate)|呼叫 以在將所有請求傳遞到[執行](#execute)後取消初始化輔助角色物件。|

|Typedef|描述|
|-------------|-----------------|
|[要求類型](#requesttype)|工兵類可以處理的工作項類型的類型類型。|

典型的*工人*類如下所示:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**現有實現**

這些類別符合此原型:

|類別|描述|
|-----------|-----------------|
|[無狀態工人](../../atl/reference/cnonstatelessworker-class.md)|從線程池接收請求,並將它們傳遞到為每個請求創建和銷毀的工作物件。|

**使用**

這些樣本參數期望類符合此原型:

|參數名稱|使用對象|
|--------------------|-------------|
|*工人*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*工人*|[無狀態工人](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>需求

**標題:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>輔助類型:執行

調用以處理工作項。

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>參數

*要求*<br/>
要處理的工作項。 工作項的類型與`RequestType`相同。

*pvWorkerParam*<br/>
輔助角色類理解的自定義參數。 也傳遞到`WorkerArchetype::Initialize`與`Terminate`。

*p 重疊*<br/>
指向[OVERLAPPED 結構](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)的指標,用於創建工作項排隊的佇列。

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>工人Arche類型::初始化

調用 以在將任何請求傳遞`WorkerArchetype::Execute`到 之前初始化輔助角色物件。

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
輔助角色類理解的自定義參數。 也傳遞到`WorkerArchetype::Terminate`與`WorkerArchetype::Execute`。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>輔助類型:請求類型

工兵類可以處理的工作項類型的類型類型。

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>備註

此類型必須用作 的第一個參數`WorkerArchetype::Execute`, 並且必須能夠強制轉換到和從ULONG_PTR。

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>工人類:終止

調用 以在將所有請求傳遞`WorkerArchetype::Execute`到 後取消初始化輔助角色物件。

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>參數

*pvParam*<br/>
輔助角色類理解的自定義參數。 也傳遞到`WorkerArchetype::Initialize`與`WorkerArchetype::Execute`。

## <a name="see-also"></a>另請參閱

[概念](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 桌面元件](../../atl/atl-com-desktop-components.md)
