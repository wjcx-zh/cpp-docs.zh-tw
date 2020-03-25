---
title: _com_ptr_t 擷取器
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
ms.openlocfilehash: 31ac39104c041d1d119f6cd06de5f9c4a620dac0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190023"
---
# <a name="_com_ptr_t-extractors"></a>_com_ptr_t 擷取器

**Microsoft 專屬**

擷取封裝的 COM 介面指標。

## <a name="syntax"></a>語法

```
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>備註

- **運算子介面**<strong>\*</strong>會傳回封裝的介面指標，可能是 Null。

- **運算子介面 &** 傳回封裝介面指標的參考，並在指標為 Null 時發出錯誤。

- **運算子**<strong>\*</strong>可讓智慧型指標物件在進行取值時，能夠如同實際的封裝介面一樣。

- **operator->** 允許智慧型指標物件在取值時，其作用就如同實際的封裝介面。

- **運算子 &** 釋放任何封裝的介面指標，以 Null 取代它，並傳回封裝之指標的位址。 這可讓智慧指標以傳址方式傳遞至函式，該函式具有*輸出*參數，可透過它傳回介面指標。

- **運算子 bool**允許在條件運算式中使用智慧型指標物件。 如果指標不是 Null，則這個運算子會傳回 TRUE。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
