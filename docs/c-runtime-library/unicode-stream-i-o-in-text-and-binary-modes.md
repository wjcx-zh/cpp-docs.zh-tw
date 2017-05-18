---
title: "文字和二進位模式的 Unicode 資料流 I-O | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: 7
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6a4658396f5045df17fbf75daac5bbf8263ed60c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>文字和二進位模式的 Unicode 資料流 I/O
Unicode 資料流 I/O 常式 (例如 `fwprintf`、`fwscanf`、`fgetwc`、`fputwc`、`fgetws` 或 `fputws`) 作業於以文字模式 (預設) 開啟的檔案時，會進行兩種字元轉換：  
  
-   Unicode 到 MBCS 或 MBCS 到 Unicode 的轉換。 Unicode 資料流 I/O 函式以文字模式運作時，會假設來源或目的資料流是一序列的多位元組字元。 因此，Unicode 資料流輸入函式會將多位元組字元轉換為寬字元 (就像呼叫 `mbtowc` 函式一樣)。 基於相同的原因，Unicode 資料流輸出函式會將寬字元轉換為多位元組字元 (就像呼叫 `wctomb` 函式一樣)。  
  
-   歸位/換行字元 (CR-LF) 轉譯。 這項轉譯是在 MBCS - Unicode 轉換 (適用於 Unicode 資料流輸入函式) 之前和 Unicode - MBCS 轉換 (適用於 Unicode 資料流輸出函式) 之後發生。 在輸入期間，每個歸位/換行字元組合都會轉譯為單一換行字元。 在輸出期間，每個換行字元都會轉譯為歸位/換行字元組合。  
  
 不過，Unicode 資料流 I/O 函式以二進位模式運作時，會假設檔案為 Unicode，而且在輸入或輸出期間不會進行 CR-LF 轉譯或字元轉換。 使用 _setmode(_fileno(stdin), _O_BINARY); 指令，以在 UNICODE 文字檔上正確地使用 wcin。  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)   
 [輸入和輸出](../c-runtime-library/input-and-output.md)
