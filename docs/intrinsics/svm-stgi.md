---
title: __svm_stgi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __svm_stgi
dev_langs:
- C++
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9346270c09a3174c2583d68cdfb62e11f5112144
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="svmstgi"></a>__svm_stgi
**Microsoft 特定的**  
  
 設定全域中斷旗標。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_stgi(void);  
```  
  
## <a name="remarks"></a>備註  
 `__svm_stgi`函數即相當於`STGI`機器指令。 全域中斷旗標會判斷微處理器會忽略，延後，或處理等 I/O 完成、 硬體溫度警示或偵錯例外狀況事件，而中斷。  
  
 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 在文件編號 24593，修訂 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_stgi`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__svm_clgi](../intrinsics/svm-clgi.md)