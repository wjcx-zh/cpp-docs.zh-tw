---
title: 初始設定式清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: 4
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 1af020bec295f0f949b7ebb6abe88102f3942b1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="initializer-lists"></a>初始設定式清單
建構函式中的初始設定式清單現在會在基底類別建構函式之前呼叫。  
  
## <a name="remarks"></a>備註  
 在 Visual c + + 2005年之前已在初始設定式清單之前呼叫基底類別建構函式編譯 Managed Extensions for c + + 時。 現在，以編譯時**/clr**，初始設定式清單呼叫第一次。  
  
## <a name="see-also"></a>請參閱  
 [一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)