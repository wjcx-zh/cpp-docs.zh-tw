---
title: "預先定義的規則 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6541dc5dc262f5d00325c594d64637b5e87a45d1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="predefined-rules"></a>預先定義的規則
預先定義的推斷規則使用 NMAKE 所提供的命令和選項巨集。  
  
|規則|命令|預設<br /><br /> action|Batch<br /><br /> 規則|Nmake 平台上執行|  
|----------|-------------|------------------------|--------------------|----------------------------|  
|。 asm.exe|$(AS) $(AFLAGS) $<|ml $<|no|x86|  
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|  
|。 asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|no|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|。 c.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|  
|。 c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|  
|。 cc.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|  
|。 cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|  
|。 cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|no|全部|  
|。 cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|全部|  
|。 cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|no|全部|  
|。 cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|全部|  
|。 rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|no|全部|  
  
## <a name="see-also"></a>另請參閱  
 [推斷規則](../build/inference-rules.md)