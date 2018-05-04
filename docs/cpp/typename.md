---
title: 類型名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- typename_cpp
dev_langs:
- C++
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6eebf038fbe3e5e18e3f2a1e8e7a2aa2554bf41
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="typename"></a>typename
在樣板定義中提供提示給編譯器未知的識別項是型別。 在樣板參數清單中，用來指定的型別參數上。  
  
## <a name="syntax"></a>語法  
  
```  
  
typename identifier;  
```  
  
## <a name="remarks"></a>備註  
 如果樣板定義中的名稱是完整的名稱是取決於樣板引數，則必須使用這個關鍵字如果限定的名稱不是相依，它是選擇性的。 如需詳細資訊，請參閱[樣板和名稱解析](../cpp/templates-and-name-resolution.md)。  
  
 **typename**可供樣板宣告或定義中的任何類型。 除非是做為範本基底類別的樣板引數，否則不允許出現在基底類別清單中。  
  
```  
template <class T>  
class C1 : typename T::InnerType // Error - typename not allowed.  
{};  
template <class T>  
class C2 : A<typename T::InnerType>  // typename OK.  
{};  
```  
  
 **Typename**關鍵字也可取代**類別**在樣板參數清單。 例如，下列陳述式是語意上相等的：  
  
```  
template<class T1, class T2>...  
template<typename T1, typename T2>...  
```  
  
## <a name="example"></a>範例  
  
```  
// typename.cpp  
template<class T> class X  
{  
   typename T::Y m_y;   // treat Y as a type  
};  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [範本](../cpp/templates-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)