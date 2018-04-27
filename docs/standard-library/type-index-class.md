---
title: type_index 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- typeindex/std::type_index
dev_langs:
- C++
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 86058cd8deb0ddd9458c8882bb31029d365cb110
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="typeindex-class"></a>type_index 類別

`type_index` 類別會將指標包裝到 [type_info Class](../cpp/type-info-class.md) 來協助這類物件的索引。

class type_index { public: type_index(const type_info& tinfo); const char *name() const; size_t hash_code() const; bool operator==(const type_info& right) const; bool operator!=(const type_info& right) const; bool operator<(const type_info& right) const; bool operator\<=(const type_info& right) const; bool operator>(const type_info& right) const; bool operator>=(const type_info& right) const; };

建構函式會將 `ptr` 初始化為 `&tinfo`。

`name` 會傳回 `ptr->name()`。

`hash_code` 傳回 `ptr->hash_code().`

`operator==` 會傳回 `*ptr == right.ptr`。

`operator!=` 會傳回 `!(*this == right)`。

`operator<` 會傳回 `*ptr->before(*right.ptr)`。

`operator<=` 傳回 `!(right < *this).`

`operator>` 會傳回 `right < *this`。

`operator>=` 會傳回 `!(*this < right)`。

## <a name="see-also"></a>另請參閱

[執行階段類型資訊](../cpp/run-time-type-information.md)<br/>
[\<typeindex>](../standard-library/typeindex.md)<br/>
