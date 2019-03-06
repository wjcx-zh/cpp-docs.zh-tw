---
title: 預先定義的規則
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: e3b30957c15d6fb4eabb72381bad43a2d622a25d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413195"
---
# <a name="predefined-rules"></a>預先定義的規則

預先定義的推斷規則會使用 NMAKE 所提供的命令和選項巨集。

|規則|命令|預設<br /><br /> action|Batch<br /><br /> 規則|在上執行的平台 nmake|
|----------|-------------|------------------------|--------------------|----------------------------|
|.asm.exe|$(AS) $(AFLAGS) $<|ml $<|否|x86|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|
|.asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|否|X64|
|.asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|X64|
|.c.exe|$(CC) $(CFLAGS) $<|cl $<|否|all|
|.c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|all|
|.cc.exe|$(CC) $(CFLAGS) $<|cl $<|否|all|
|.cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|all|
|.cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|否|all|
|.cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|all|
|.cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|否|all|
|.cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|all|
|.rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|否|all|

## <a name="see-also"></a>另請參閱

[推斷規則](../build/inference-rules.md)
