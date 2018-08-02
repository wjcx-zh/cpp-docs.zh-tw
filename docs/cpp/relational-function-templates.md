---
title: 關係函式樣板 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- relational function templates
ms.assetid: 57893a51-9adb-41fc-941d-2ca97687db2a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96fd147214b80002eb2fba60ce046072e8c9e842
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461639"
---
# <a name="relational-function-templates"></a>關係函式樣板
**Microsoft 專屬**  
  
## <a name="syntax"></a>語法  
  
```  
template<typename _InterfaceType> bool operator==(  
   int NULL,  
   _com_ptr_t<_InterfaceType>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator==(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
template<typename _Interface> bool operator!=(  
   int NULL,  
   _com_ptr_t<_Interface>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator!=(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
template<typename _Interface> bool operator<(  
   int NULL,  
   _com_ptr_t<_Interface>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator<(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
template<typename _Interface> bool operator>(  
   int NULL,  
   _com_ptr_t<_Interface>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator>(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
template<typename _Interface> bool operator<=(  
   int NULL,  
   _com_ptr_t<_Interface>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator<=(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
template<typename _Interface> bool operator>=(  
   int NULL,  
   _com_ptr_t<_Interface>& p   
);  
template<typename _Interface,  
   typename _InterfacePtr> bool operator>=(  
   _Interface* i,  
   _com_ptr_t<_InterfacePtr>& p   
);  
```  
  
### <a name="parameters"></a>參數  
 *i*  
 原始的介面指標。  
  
 *p*  
 智慧型指標。  
  
## <a name="remarks"></a>備註  
 這些函式樣板可以與比較運算子右側的智慧型指標進行比較。 這些都不是 `_com_ptr_t` 的成員函式。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_ptr_t 類別](../cpp/com-ptr-t-class.md)