---
title: 編譯器錯誤 C2338 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2338
dev_langs:
- C++
helpviewer_keywords:
- C2338
ms.assetid: 49bba575-1de4-4963-86c6-ce3226a2ba51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 156074f20517c1d2e2f4fdb4ac5c54d6cf014276
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222302"
---
# <a name="compiler-error-c2338"></a>編譯器錯誤 C2338  
  
> *錯誤訊息*  
  
這個錯誤可能因`static_assert`編譯期間發生錯誤。 訊息由提供`static_assert`參數。   
  
編譯器的外部提供者也可以產生這個錯誤訊息。 在大部分情況下，屬性提供者 DLL，例如 ATLPROV 報告這些錯誤。 此訊息的一些常見的形式包括：

> '*屬性*' Atl 屬性提供者： 錯誤 ATL*數目**訊息*  
  
> 屬性使用方式不正確 '*屬性*'
  
> '*使用量*': 屬性 '使用' 的格式不正確  
  
這些錯誤通常是無法復原，並且後面可以跟著嚴重編譯器錯誤。  
  
若要修正這些問題，更正屬性使用方式。 例如，在某些情況下，屬性必須宣告參數才能使用。 如果提供 ATL 錯誤號碼，請檢查該錯誤，以取得更多相關資訊的文件。  
