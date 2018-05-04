---
title: -範圍 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d06d699500ba3ea441af61a2e2a5a0da3f96903a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
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
 若要查看映像的虛擬位址，對應檔映像中使用 （RVA + 基底） **/DISASM**或 **/HEADERS** dumpbin 或反組譯碼視窗的 Visual Studio 偵錯工具中的選項。  
  
## <a name="example"></a>範例  
 在此範例中， **/範圍**用來修改顯示 **/disasm**選項。 在此範例中，起始的值會表示為十進位數字和結束值指定為十六進位數字。  
  
```  
dumpbin /disasm /range:4219334,0x004061CD t.exe  
```  
  
## <a name="see-also"></a>另請參閱  
 [DUMPBIN 選項](../../build/reference/dumpbin-options.md)