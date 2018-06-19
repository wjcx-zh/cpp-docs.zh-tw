---
title: _bstr_t 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _bstr_t
dev_langs:
- C++
helpviewer_keywords:
- BSTR object
- _bstr_t class
- BSTR object [C++], COM encapsulation
ms.assetid: 58841fef-fe21-4a84-aab9-780262b5201f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bea9f863df08342f17419a16b14579fa6a257b8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415279"
---
# <a name="bstrt-class"></a>_bstr_t 類別
**Microsoft 特定的**  
  
 A`_bstr_t`物件封裝[BSTR 資料類型](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)。 這個類別會管理資源配置和解除配置函式呼叫來透過**SysAllocString**和**SysFreeString**和其他`BSTR`Api 在適當的情況。 `_bstr_t` 類別會使用參考計數避免過多的額外負荷。  
  
### <a name="construction"></a>建構  
  
|||  
|-|-|  
|[_bstr_t](../cpp/bstr-t-bstr-t.md)|建構 `_bstr_t` 物件。|  
  
### <a name="operations"></a>作業  
  
|||  
|-|-|  
|[指派](../cpp/bstr-t-assign.md)|將 `BSTR` 複製到 `BSTR` 所包裝的 `_bstr_t` 中。|  
|[Attach](../cpp/bstr-t-attach.md)|將 `_bstr_t` 包裝函式連結至 `BSTR`。|  
|[copy](../cpp/bstr-t-copy.md)|建構已封裝 `BSTR` 的複本。|  
|[Detach](../cpp/bstr-t-detach.md)|傳回 `BSTR` 所包裝的 `_bstr_t`，並將 `BSTR` 與 `_bstr_t` 中斷連結。|  
|[GetAddress](../cpp/bstr-t-getaddress.md)|指向 `BSTR` 所包裝的 `_bstr_t`。|  
|[GetBSTR](../cpp/bstr-t-getbstr.md)|指向由 `BSTR` 所包裝之 `_bstr_t` 的開頭。|  
|[length](../cpp/bstr-t-length.md)|傳回 `_bstr_t` 中的字元數。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator =](../cpp/bstr-t-operator-equal.md)|將新值指派給現有的 `_bstr_t` 物件。|  
|[運算子 + =](../cpp/bstr-t-operator-add-equal-plus.md)|將字元附加至 `_bstr_t` 物件的結尾。|  
|[運算子 +](../cpp/bstr-t-operator-add-equal-plus.md)|串連兩個字串。|  
|[運算子 !](../cpp/bstr-t-operator-logical-not.md)|如果會檢查封裝`BSTR`是**NULL**字串。|  
|[運算子 = =、 ！ =、 \<，>， \<=、 > =](../cpp/bstr-t-relational-operators.md)|比較兩個 `_bstr_t` 物件。|  
|[運算子 wchar_t * &#124; char\*](../cpp/bstr-t-wchar-t-star-bstr-t-char-star.md)|將指標擷取至封裝的 Unicode 或多位元組的 `BSTR` 物件。|  
  
**結束 Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** \<comutil.h >  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)