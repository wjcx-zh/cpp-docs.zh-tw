---
title: "&lt;ostream&gt; 運算子 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ostream/std::operator&lt;&lt;
dev_langs: C++
ms.assetid: 9282a62e-a3d1-4371-a284-fbc9515bb9a2
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f78befe92263dd6b4ef666c865ef9dd65c7103db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ltostreamgt-operators"></a>&lt;ostream&gt; 運算子
||  
|-|  
|[operator&lt;&lt;](#op_lt_lt)|  
  
##  <a name="op_lt_lt"></a> operator&lt;&lt;  
 將各種類型寫入資料流。  
  
```
template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const Elem* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    Elem _Ch);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    const char* str);

template <class _Elem, class _Tr>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>& _Ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _ostr,
    char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char* str);

template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);

template <class _Elem, class _Tr, class T>
basic_ostream <_Elem, _Tr>& operator<<(
    basic_ostream<_Elem, _Tr>&& _Ostr,
    Ty val);
```  
  
### <a name="parameters"></a>參數  
 `_Ch`  
 字元。  
  
 `_Elem`  
 元素類型。  
  
 `_Ostr`  
 `basic_ostream` 物件。  
  
 `str`  
 字元字串。  
  
 `_Tr`  
 字元特性。  
  
 `val`  
 類型  
  
### <a name="return-value"></a>傳回值  
 資料流。  
  
### <a name="remarks"></a>備註  
 `basic_ostream` 類別也會定義數個插入運算子。 如需詳細資訊，請參閱 [basic_ostream::operator&lt;&lt;](../standard-library/basic-ostream-class.md#basic_ostream_operator_lt_lt)。  
  
 樣板函式  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _ostr,
    const Elem *str);
```  
  
 決定開頭位於 `str` 之序列的長度 N = `traits_type::`[length](../standard-library/char-traits-struct.md#length)( `str`)，然後插入序列。 如果 N < `_Ostr.`[width](../standard-library/ios-base-class.md#width)，則函式會另外插入重複的 `_Ostr.width` - N 填滿字元。 在以下情況重複項目會排在序列之前：當 (`_Ostr`. [flags](../standard-library/ios-base-class.md#flags) & `adjustfield` != [left](../standard-library/ios-functions.md#left)。 否則，重複項目會接在序列後面。 函式會傳回 `_Ostr`。  
  
 樣板函式  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 插入項目 `_Ch`。 如果 1 < `_Ostr.width`，則函式會另外插入 `_Ostr.width` - 1 填滿字元的重複項目。 在以下情況重複項目會排在序列之前：當 `_Ostr.flags & adjustfield != left`。 否則，重複項目會接在序列後面。 它會傳回 `_Ostr`。  
  
 樣板函式  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const char *str);
```  
  
 行為相同於  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 不同之處在於開頭位於 `str` 之序列的每個項目 `_Ch` 會呼叫 `_Ostr.`[put](../standard-library/basic-ostream-class.md#put)( `_Ostr.`[widen](../standard-library/basic-ios-class.md#widen)( `_Ch`)) 來轉換為類型 `Elem` 的物件。  
  
 樣板函式  
  
```cpp
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    char _Ch);
```  
  
 行為相同於  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 不同之處在於 `_Ch` 會呼叫 `_Ostr.put`( `_Ostr.widen`( `_Ch`)) 來轉換為類型 `Elem` 的物件。  
  
 樣板函式  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const char *str);
```  
  
 行為相同於  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    const Elem *str);
```  
  
 (插入項目之前並不需要擴展項目)。  
  
 樣板函式  
  
```cpp  
template <class _Tr>
basic_ostream<char, Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    char _Ch);
```  
  
 行為相同於  
  
```cpp  
template <class _Elem, class _Tr>
basic_ostream<Elem, _Tr>& operator<<(
    basic_ostream<Elem, _Tr>& _Ostr,
    Elem _Ch);
```  
  
 (插入 `_Ch` 之前並不需要擴展它)。  
  
 樣板函式  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const signed char *str);
```  
  
 傳回 `_Ostr` << ( `const char *`) `str`。  
  
 樣板函式  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    signed char _Ch);
```  
  
 傳回 `_Ostr` << ( `char`) `_Ch`。  
  
 範本函式：  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    const unsigned char *str);
```  
  
 傳回 `_Ostr` << ( `const char *`) `str`。  
  
 範本函式：  
  
```cpp  
template <class _Tr>
basic_ostream<char, _Tr>& operator<<(
    basic_ostream<char, _Tr>& _Ostr,
    unsigned char _Ch);
```  
  
 傳回 `_Ostr` << ( `char`) `_Ch`。  
  
 樣板函式：  
  
```cpp  
template <class _Elem, class _Tr, class T>
basic_ostream<_Elem, _Tr>& operator<<(
    basic_ostream<char, _Tr>&& _Ostr,
    T val);
```  
  
 傳回 `_Ostr` `<<` `val` (並轉換[右值參考](../cpp/rvalue-reference-declarator-amp-amp.md)為 `_Ostr` 到程序中的左值)。  
  
### <a name="example"></a>範例  
  如需 `operator<<` 的使用範例，請參閱 [flush](../standard-library/ostream-functions.md#flush)。  
  
## <a name="see-also"></a>請參閱  
 [\<ostream>](../standard-library/ostream.md)



