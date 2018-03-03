---
title: "嚴重錯誤 C1067 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8889ccbfcac31917948da719444dab68a2d1b9c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1067"></a>嚴重錯誤 C1067
編譯器限制： 已超過類型記錄的大小的 64k 限制  
  
 如果符號己超過 247 個字元的裝飾的名稱，可能發生這個錯誤。  若要解決，請縮短符號名稱。  
  
 當編譯器產生偵錯資訊時，它會發出型別記錄來定義在原始程式碼中遇到的型別。  例如，型別記錄包含簡單的結構和函式的引數清單。  這些類型的記錄部分可以是大型清單。  
  
 任何型別記錄的大小沒有 64k 的限制。  如果超過 64k 限制會發生此錯誤。  
  
 如果有許多長名稱的符號或有太多成員的類別、 結構或等位，也會發生 C1067。