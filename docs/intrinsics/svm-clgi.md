---
title: "__svm_clgi |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_clgi
dev_langs: C++
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fe7aacf6a337235e40c9d681ddce1928fe28c2e
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2018
---
# <a name="svmclgi"></a>__svm_clgi
**Microsoft 特定的**  
  
 清除全域中斷旗標。  
  
## <a name="syntax"></a>語法  
  
```  
void __svm_clgi( void );  
```  
  
## <a name="remarks"></a>備註  
 `__svm_clgi`函數即相當於`CLGI`機器指令。 全域中斷旗標會判斷微處理器會忽略，延後，或處理等 I/O 完成、 硬體溫度警示或偵錯例外狀況事件，而中斷。  
  
 這個函式支援主機虛擬機器監視器與客體作業系統及其應用程式的互動。 如需詳細資訊，搜尋文件中，"AMD64 架構程式設計人員手動磁碟區 2： 系統程式設計中，「 在文件編號 24593，修訂 3.11， [AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站台。  
  
## <a name="requirements"></a>需求  
  
|內建|架構|  
|---------------|------------------|  
|`__svm_clgi`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **標頭檔** \<intrin.h >  
  
**結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [編譯器內建函式](../intrinsics/compiler-intrinsics.md)   
 [__svm_stgi](../intrinsics/svm-stgi.md)