---
title: 預先定義的規則
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: 7a922a239306f10121791caa8f9f088cea88c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319443"
---
# <a name="predefined-rules"></a>預先定義的規則

預先定義的推斷規則會使用 NMAKE 所提供的命令和選項巨集。

|規則|命令|預設<br /><br /> action|Batch<br /><br /> 規則|在上執行的平台 nmake|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml $<|否|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|
|.asm.exe|$(AS) $(AFLAGS) $&LT;|ml64 $<|否|X64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|X64|
|.c.exe|$(CC) $(CFLAGS) $&LT;|cl $<|否|all|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|all|
|.cc.exe|$(CC) $(CFLAGS) $&LT;|cl $<|否|all|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|all|
|.cpp.exe|$(CPP) $(CPPFLAGS) $&LT;|cl $<|否|all|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|all|
|.cxx.exe|$(CXX) $(CXXFLAGS) $&LT;|cl $<|否|all|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|all|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc 的 /r $<|否|all|

## <a name="see-also"></a>另請參閱

[推斷規則](inference-rules.md)
