---
title: 編譯器警告 （層級 1） C4678 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81eb7df618f97300c2654cc0f4f7a58d18215b26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076095"
---
# <a name="compiler-warning-level-1-c4678"></a>編譯器警告 (層級 1) C4678

基底類別 'base_type' 比 'derived_type' 更難以存取

公用類型衍生自私用類型。 如果在參考的組件中具現化公用類型，則無法存取私用基底類型成員。

連接 C4678 才可使用過時的編譯器選項 **/clr: oldsyntax**。 使用時，即為錯誤 **/clr**、 能夠存取的基底類別，其衍生的類別。
