---
title: "編譯器警告 （層級 1） C4819 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4819
dev_langs: C++
helpviewer_keywords: C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b515a3f5e840bbc93f37420866023ee778b404ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4819"></a>編譯器警告 (層級 1) C4819
檔案包含無法在目前字碼頁 (數字) 中表示的字元。 請以 Unicode 格式儲存檔案，以防止資料遺失。  
  
 在字碼頁無法表示檔案中所有字元的系統上編譯 ANSI 原始程式檔時，就會發生 C4819。  
  
 若要解決 C4819，請以 Unicode 格式儲存檔案。 在 Visual Studio 中，選擇 **檔案**，**進階儲存選項**。 中**進階儲存選項**對話方塊方塊中，選取可代表檔案中的所有字元的編碼方式 — 比方說，utf-8，然後選擇  **確定**。