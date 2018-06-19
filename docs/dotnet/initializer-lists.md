---
title: 初始設定式清單 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- initializer lists
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6634b749480e5108548de0c8b53f8b09cc5a42c2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33127948"
---
# <a name="initializer-lists"></a>初始設定式清單
建構函式中的初始設定式清單現在會在基底類別建構函式之前呼叫。  
  
## <a name="remarks"></a>備註  
 在 Visual c + + 2005年之前已在初始設定式清單之前呼叫基底類別建構函式編譯 Managed Extensions for c + + 時。 現在，以編譯時 **/clr**，初始設定式清單呼叫第一次。  
  
## <a name="see-also"></a>另請參閱  
 [一般的語言變更 (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)