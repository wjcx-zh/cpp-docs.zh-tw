---
title: _com_ptr_t 擷取器
description: 描述 _com_ptr_t 類別的抽取運算子。
ms.date: 07/07/2020
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
ms.openlocfilehash: fb5441d87dc35ec6fbb495bc38d9041c1f2d2f33
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220570"
---
# <a name="_com_ptr_t-extractors"></a>`_com_ptr_t`擷取器

**Microsoft 特定**

擷取封裝的 COM 介面指標。

## <a name="syntax"></a>語法

```c++
operator Interface*( ) const throw( );
operator Interface&( ) const;
Interface& operator*( ) const;
Interface* operator->( ) const;
Interface** operator&( ) throw( );
operator bool( ) const throw( );
```

## <a name="remarks"></a>備註

- **`operator Interface*`** 傳回封裝的介面指標，可能是 Null。

- **`operator Interface&`** 傳回封裝介面指標的參考，並在指標為 Null 時發出錯誤。

- **`operator*`** 允許智慧型指標物件在取值時，其作用就如同實際的封裝介面。

- **`operator->`** 允許智慧型指標物件在取值時，其作用就如同實際的封裝介面。

- **`operator&`** 釋放任何封裝的介面指標，以 Null 取代它，並傳回封裝之指標的位址。 這個運算子可讓您將智慧型指標 by 位址傳遞給具有*out*參數的函式，其會透過它傳回介面指標。

- **`operator bool`** 允許在條件運算式中使用智慧型指標物件。 **`true`** 如果指標不是 Null，則這個運算子會傳回。

  > [!NOTE]
  > 因為不 **`operator bool`** 是宣告為 **`explicit`** ，所以 `_com_ptr_t` 會隱含地轉換為 **`bool`** ，其可轉換為任何純量類型。 這在您的程式碼中可能會產生非預期的結果。 啟用[編譯器警告（層級4） C4800](../error-messages/compiler-warnings/compiler-warning-level-3-c4800.md) ，以防止意外使用此轉換。

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
