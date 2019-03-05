---
title: context_unblock_unbalanced 類別
ms.date: 11/04/2016
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
ms.openlocfilehash: f4f385cde2a27665afa5eb9869eb52bc42c70111
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283991"
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced 類別

這個類別描述時所擲回的例外狀況呼叫`Block`並`Unblock`方法`Context`物件未正確配對。

## <a name="syntax"></a>語法

```
class context_unblock_unbalanced : public std::exception;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[context_unblock_unbalanced](#ctor)|多載。 建構 `context_unblock_unbalanced` 物件。|

## <a name="remarks"></a>備註

若要呼叫`Block`並`Unblock`方法`Context`物件必須永遠正確配對。 並行執行階段可讓任何一種順序進行的作業。 例如，呼叫 `Block` 之後可以呼叫 `Unblock`，反之亦然。 如果執行個體，兩個呼叫會擲回這個例外狀況`Unblock`方法進行了在資料列，`Context`物件已不會被封鎖。

## <a name="inheritance-hierarchy"></a>繼承階層

`exception`

`context_unblock_unbalanced`

## <a name="requirements"></a>需求

**標頭：** concrt.h

**命名空間：** concurrency

##  <a name="ctor"></a> context_unblock_unbalanced

建構 `context_unblock_unbalanced` 物件。

```
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

context_unblock_unbalanced() throw();
```

### <a name="parameters"></a>參數

*_Message*<br/>
錯誤的描述性訊息。

## <a name="see-also"></a>另請參閱

[concurrency 命名空間](concurrency-namespace.md)
