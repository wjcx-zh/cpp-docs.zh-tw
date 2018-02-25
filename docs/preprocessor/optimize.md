---
title: "最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.optimize
- optimize_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, optimize
- optimize pragma
ms.assetid: cb13c1cc-186a-45bc-bee7-95a8de7381cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ae1988292b1f6dfa35f4cb77d145641528ed827f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="optimize"></a>optimize
指定要依照函式逐一執行的最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
  
#pragma optimize( "[optimization-list]", {on | off} )  
```  
  
## <a name="remarks"></a>備註  
 **最佳化**pragma 必須出現在函式之外，並在第一個顯示該 pragma 後定義的函式生效。 **上**和**關閉**引數開啟選項中指定*最佳化清單*開啟或關閉。  
  
 *最佳化清單*可以是零或多個參數下, 表所示。  
  
### <a name="parameters-of-the-optimize-pragma"></a>最佳化 Pragma 的參數  
  
|參數|最佳化類型|  
|--------------------|--------------------------|  
|**g**|啟用全域最佳化。|  
|**s**或**t**|指定機器碼的短 (short) 序列或快速 (fast) 序列。|  
|**y**|在程式堆疊上產生框架指標。|  
  
 這些是與所用的相同字母[/O](../build/reference/o-options-optimize-code.md)編譯器選項。 例如，下列 pragma 相當於**/Os**編譯器選項：  
  
```  
#pragma optimize( "ts", on )  
```  
  
 使用**最佳化**pragma 搭配空字串 (**""**) 是一種特殊形式的指示詞：  
  
 當您使用**關閉**參數時，會將最佳化，關閉稍早在本主題中，資料表中列出。  
  
 當您使用**上**參數，會重設為最佳化，您指定了與[/O](../build/reference/o-options-optimize-code.md)編譯器選項。  
  
```  
#pragma optimize( "", off )  
.  
.  
.  
#pragma optimize( "", on )   
```  
  
## <a name="see-also"></a>請參閱  
 [Pragma 指示詞和 __Pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)