---
title: "編譯器錯誤 C3859 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3859
dev_langs:
- C++
helpviewer_keywords:
- C3859
ms.assetid: 40e93b25-4393-4467-90de-035434a665c7
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8a132eb7dbf09421ad5c99249b0208e5f901156b
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3859"></a>編譯器錯誤 C3859
超出 PCH 的虛擬記憶體範圍；請使用等於或大於 '-Zmvalue' 的命令列選項重新編譯  
  
 先行編譯標頭檔對編譯器正在嘗試放入其中的資料量而言太小。 使用**/Zm**編譯器旗標，指定較大的值為先行編譯標頭檔。 如需詳細資訊，請參閱[/Zm （指定先行編譯標頭的記憶體配置上限）](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)。
