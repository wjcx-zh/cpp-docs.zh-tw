---
title: bad_function_call 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f9055729d02dd16fb66028bb2c3cbc4d70168e4
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="badfunctioncall-class"></a>bad_function_call 類別

報告錯誤的函式呼叫。

## <a name="syntax"></a>語法

```cpp
class bad_function_call
 : public std::exception {
 };
```

## <a name="remarks"></a>備註

此類別描述所擲回的例外狀況，表示對 [function 類別](../standard-library/function-class.md)的 `operator()` 呼叫。
