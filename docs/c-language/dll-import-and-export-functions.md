---
title: "DLL 匯入及匯出函式 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 78d1dacd764a7d171c9cacb54a64fab241f8603a
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="dll-import-and-export-functions"></a>DLL 匯入及匯出函式
**Microsoft 特定的**  
  
 如需此主題更完整及最新的詳細資訊，請參閱 [dllexport、dllimport](../cpp/dllexport-dllimport.md)。  
  
 **dllimport** 和 `dllexport` 儲存類別修飾詞是 Microsoft 專有的 C 語言擴充功能。 這些修飾詞明確定義用戶端的 DLL 介面 (可執行檔或另一個 DLL)。 將函式宣告為 `dllexport` 即不需要使用模組定義 (.DEF) 檔。 您也可以搭配資料和物件使用 **dllimport** 和 `dllexport` 修飾詞。  
  
 **dllimport** 和 `dllexport` 儲存類別修飾詞必須搭配擴充屬性語法關鍵字 (`__declspec`) 使用，如下列範例所示：  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 如需擴充儲存類別修飾詞語法的特定資訊，請參閱[擴充的儲存類別屬性](../c-language/c-extended-storage-class-attributes.md)。  
  
 **END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [C 函式定義](../c-language/c-function-definitions.md)
