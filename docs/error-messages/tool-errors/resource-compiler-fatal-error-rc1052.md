---
title: 資源編譯器嚴重錯誤 RC1052 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1052
dev_langs:
- C++
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e0651f8c2b48ea69e7137ffa3415ddaffd8fe44
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319906"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>資源編譯器嚴重錯誤 RC1052
編譯器限制：#if 或 #ifdef 區塊巢狀結構太深  
  
 程式已超過對於 `#if` 和 `#ifdef` 指示詞允許的巢狀層次上限。  
  
 這個錯誤可能是因為包含使用這些前置處理器指示詞的檔案所造成。  
  
 若要修正這個問題，請減少資源檔中的巢狀 `#if` 和 `#ifdef` 指示詞數目。 如果問題是因為資源檔中所包含的標頭檔所造成，請減少標頭檔中的巢狀 `#if` 和 `#ifdef` 指示詞數目。 如果實際上不可行，請考慮在現有已包含的標頭檔上執行前置處理器，在資源檔中建立並包含新的標頭檔。 如需詳細資訊，請參閱[/P （前置處理至檔案）](../../build/reference/p-preprocess-to-a-file.md)編譯器選項。