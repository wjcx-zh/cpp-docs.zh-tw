---
title: '&lt;new&gt; typedef | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
caps.latest.revision: 7
manager: ghogen
ms.openlocfilehash: 53a13168986171d3240cc15e405fc08b3db07e96
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedef

||
|-|
|[new_handler](#new_handler)|

## <a name="new_handler"></a>  new_handler

此類型會指向適合用來作為新處理常式的函式。

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>備註

當 **operatornew** 或 `operator new[]` 無法滿足提供額外儲存體的要求時，便會呼叫此類型的處理常式函式。

### <a name="example"></a>範例

如需使用 `new_handler` 作為傳回值的範例，請參閱 [set_new_handler](../standard-library/new-functions.md#set_new_handler)。

## <a name="see-also"></a>另請參閱

[\<new>](../standard-library/new.md)<br/>
