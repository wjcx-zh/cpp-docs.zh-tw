---
title: raw_interfaces_only |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_interfaces_only
dev_langs:
- C++
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f217c0dad3bf74ab930cf1f66392fe22d9df832
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446544"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C + + 特定**  
  
隱藏的錯誤處理的包裝函式產生及[屬性](../cpp/property-cpp.md)使用這些包裝函式的宣告。  
  
## <a name="syntax"></a>語法  
  
```  
raw_interfaces_only  
```  
  
## <a name="remarks"></a>備註  
 
**Raw_interfaces_only**屬性也會造成用於命名非屬性函式會移除預設前置詞。 一般來說，前置詞是**raw_**。 如果指定這個屬性，函式名稱會直接來自類型程式庫。  
  
這個屬性只能讓您公開類型程式庫中的低階內容。  
  
**END c + + 特定的**  
  
## <a name="see-also"></a>另請參閱  
 
[#import 屬性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指示詞](../preprocessor/hash-import-directive-cpp.md)