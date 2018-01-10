---
title: "儲存類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a4385515becbb32b256b2bf6562af941371ef47e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="storage-class"></a>儲存類別
函式定義中的儲存類別指定名稱會為函式提供 `extern` 或 **static** 儲存類別。  
  
## <a name="syntax"></a>語法  
 *function-definition*:  
 *declaration-specifiers* opt*attribute-seq* opt*declarator declaration-list* opt*compound-statement*  
  
 /\* *attribute-seq* 是 Microsoft 專有 */  
  
 *declaration-specifiers*：  
 *storage-class-specifier declaration-specifiers* opt  
  
 *type-specifier declaration-specifiers* opt  
  
 *type-qualifier declaration-specifiers* opt  
  
 *storage-class-specifier*: /\* 用於函式定義 \*/  
 **extern**  
  
 **static**  
  
 如果函式定義未包含 *storage-class-specifier*，則儲存類別會預設為 `extern`。 您可以將函式明確宣告為 `extern`，但其實不需要。  
  
 如果函式的宣告包含 *storage-class-specifier* `extern`，則識別項的連結會與具有檔案範圍之識別項的任何可見宣告相同。 如果沒有具有檔案範圍的可見宣告，表示識別項具有外部連結。 如果識別項具有檔案範圍，但沒有 *storage-class-specifier*，表示識別項具有外部連結。 外部連結是指，識別項的每個執行個體表示相同的物件或函式。 如需連結和檔案範圍的詳細資訊，請參閱[存留期、範圍、可視性和連結](../c-language/lifetime-scope-visibility-and-linkage.md)。  
  
 具有 `extern` 以外之儲存類別規範的區塊範圍函式宣告會產生錯誤。  
  
 具有 **static** 儲存類別的函式，只有在本身定義所在的原始程式檔中才可見。 所有其他函式無論擁有明確或隱含指定的 `extern` 儲存類別，在程式的所有原始程式檔中都可見。 如果需要 **static** 儲存類別，則必須在第一個函式宣告 (如果有的話) 上宣告，以及在函式定義上宣告。  
  
 **Microsoft 特定的**  
  
 已啟用 Microsoft 擴充功能時，如果函式定義位於相同的原始程式檔中且定義明確指定了 **static** 儲存類別，則會為原本宣告時沒有儲存類別 (或具有 `extern` 儲存類別) 的函式指定 **static** 儲存類別。  
  
 使用 /Ze 編譯器選項進行編譯時，在區塊內使用 `extern` 關鍵字宣告的函式會具有全域可視性。 但使用 /Za 編譯時就不是這種情況。 如果將原始程式碼的可攜性納入考量，則不應倚賴這項功能。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>請參閱  
 [C 函式定義](../c-language/c-function-definitions.md)