---
title: 'Hstring:: Hstring 建構函式 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96b77ec87e3219206d353f56293fc201c46f5d7e
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39568767"
---
# <a name="hstringhstring-constructor"></a>HString::HString 建構函式
初始化的新執行個體**HString**類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *hstr*  
 HSTRING 控制代碼。  
  
 *other*  
 將現有**HString**物件。  
  
## <a name="remarks"></a>備註  
 第一個建構函式初始化新**HString**是空的物件。  
  
 第二個建構函式初始化新**HString**的現有值的物件*其他*參數，然後終結*其他*參數。  
  
## <a name="requirements"></a>需求  
 **標頭：** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers  
  
## <a name="see-also"></a>另請參閱  
 [HString 類別](../windows/hstring-class.md)