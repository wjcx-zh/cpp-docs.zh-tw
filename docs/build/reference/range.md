---
title: "-範圍 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ccca814a388a458513773247f79cecf87fcdeae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="range"></a>/RANGE
修改當搭配其他 dumpbin 選項，例如 /RAWDATA 或 /DISASM dumpbin 的輸出。  
  
## <a name="syntax"></a>語法  
  
```  
/RANGE:vaMin[,vaMax]  
```  
  
## <a name="flags"></a>旗標  
 **vaMin**  
 要開始 dumpbin 操作虛擬位址。  
  
 **vaMax** （選擇性）  
 想要結束的 dumpbin 作業虛擬位址。 如果未指定，dumpbin 會移至檔案結尾。  
  
## <a name="remarks"></a>備註  
 若要查看映像的虛擬位址，對應檔映像中使用 （RVA + 基底） **/DISASM**或**/HEADERS** dumpbin 或反組譯碼視窗的 Visual Studio 偵錯工具中的選項。  
  
## <a name="example"></a>範例  
 在此範例中， **/範圍**用來修改顯示**/disasm**選項。 在此範例中，起始的值會表示為十進位數字和結束值指定為十六進位數字。  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)