---
title: 預設訊號 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- default signals
- defaults, signals
ms.assetid: db9fc17b-75c0-4d33-86be-c536584bbede
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4295c0fbd0542ad6c7c819b6ef7024b2384304d5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="default-signals"></a>預設訊號
**ANSI 4.7.1.1** 如果沒有在呼叫訊號處理常式之前執行 **signal (***sig***, SIG_DFL)** 的同等項，會封鎖所執行的訊號  
  
 在程式開始執行時，訊號會設定為其預設狀態。  
  
## <a name="see-also"></a>另請參閱  
 [程式庫函式](../c-language/library-functions.md)