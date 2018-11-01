---
title: 預先定義的規則
ms.date: 11/04/2016
helpviewer_keywords:
- rules, predefined
- NMAKE program, predefined rules
- predefined rules in NMAKE
ms.assetid: 638cdc3f-4aba-4b4f-96e3-ad65b0364f12
ms.openlocfilehash: b4b8ca7b0126ca42b2144aa094e7f766f6344b2a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609686"
---
# <a name="predefined-rules"></a>預先定義的規則

預先定義的推斷規則會使用 NMAKE 所提供的命令和選項巨集。

|規則|命令|預設<br /><br /> action|Batch<br /><br /> 規則|在上執行的平台 nmake|
|----------|-------------|------------------------|--------------------|----------------------------|
|。 asm.exe|$(AS) $(AFLAGS) $<|ml $<|否|x86|
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml /c $<|是|x86|
|。 asm.exe|$(AS) $(AFLAGS) $<|ml64 $<|否|X64|
|。 asm.obj|$(AS) $(AFLAGS) /c $<|ml64 /c $<|是|X64|
|。 c.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|
|。 c.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|。 cc.exe|$(CC) $(CFLAGS) $<|cl $<|no|全部|
|。 cc.obj|$(CC) $(CFLAGS) /c $<|cl /c $<|是|全部|
|。 cpp.exe|$(CPP) $(CPPFLAGS) $<|cl $<|no|全部|
|。 cpp.obj|$(CPP) $(CPPFLAGS) /c $<|cl /c $<|是|全部|
|。 cxx.exe|$(CXX) $(CXXFLAGS) $<|cl $<|no|全部|
|。 cxx.obj|$(CXX) $(CXXFLAGS) /c $<|cl /c $<|是|全部|
|。 rc.res|$(RC) $(RFLAGS) /r $<|rc /r $<|否|全部|

## <a name="see-also"></a>另請參閱

[推斷規則](../build/inference-rules.md)