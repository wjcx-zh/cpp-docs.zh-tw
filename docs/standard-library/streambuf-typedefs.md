---
title: '&lt;streambuf&gt; typedef | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8a11f21fc55babc7c71bb312bc582719f532347a
ms.lasthandoff: 02/24/2017

---
# <a name="ltstreambufgt-typedefs"></a>&lt;streambuf&gt; typedef
|||  
|-|-|  
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|  
  
##  <a name="a-namestreambufa--streambuf"></a><a name="streambuf"></a>  streambuf  
 會使用 `char` 做為範本參數的 `basic_streambuf` 特製化。  
  
```
typedef basic_streambuf<char, char_traits<char>> streambuf;
```  
  
### <a name="remarks"></a>備註  
 這個類型與 [basic_streambuf](../standard-library/basic-streambuf-class.md) 同義，已針對具有預設字元特性的 `char` 類型項目進行特製化。  
  
##  <a name="a-namewstreambufa--wstreambuf"></a><a name="wstreambuf"></a>  wstreambuf  
 會使用 `wchar_t` 做為範本參數的 `basic_streambuf` 特製化。  
  
```
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```  
  
### <a name="remarks"></a>備註  
 這個類型與 [basic_streambuf](../standard-library/basic-streambuf-class.md) 同義，已針對具有預設字元特性的 `wchar_t` 類型項目進行特製化。  
  
## <a name="see-also"></a>另請參閱  
 [\<streambuf>](../standard-library/streambuf.md)




