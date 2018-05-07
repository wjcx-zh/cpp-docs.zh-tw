---
title: 資源編譯器嚴重錯誤 RC1018 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1018
dev_langs:
- C++
helpviewer_keywords:
- RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc54586d03aaf84882120cee0428990caa8cae97
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1018"></a>資源編譯器嚴重錯誤 RC1018
未預期 ' #elif'  
  
 `#elif`指示詞未出現在`#if`， **#ifdef**，或 **#ifndef**建構。  
  
 請確定沒有`#if`， **#ifdef**，或 **#ifndef**這個陳述式前的作用中陳述式。