---
title: "編譯器警告 （層級 1） C4951 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: da1b8904a6daf8e356cf65bb80f0fd36f467a35f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4951"></a>編譯器警告 (層級 1) C4951
由於已收集設定檔資料，因此 'function' 已編輯，但未使用函式設定檔資料  
  
 若要將輸入模組中編輯函式[除了](../../build/reference/ltcg-link-time-code-generation.md)，好讓分析資料現在無效。 輸入模組在 **/LTCG:PGINSTRUMENT** 之後已重新編譯，且相較於***/LTCG:PGINSTRUMENT***作業當時模組中的控制流程，輸入模組的函式 ( **function** ) 的控制流程不同。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 **/LTCG:PGINSTRUMENT**，再取消復原所有測試回合，並執行 **/LTCG:PGOPTIMIZE**。  
  
 如果已使用 **/LTCG:PGOPTIMIZE** ，則這個警告會變成錯誤。
