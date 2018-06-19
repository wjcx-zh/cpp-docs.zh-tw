---
title: 開發您自己的 Helper 函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- helper functions
ms.assetid: a845429d-68b1-4e14-aa88-f3f5343bd490
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6b8e397fecc8f14140cd7c86217421d5aa1a749
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371394"
---
# <a name="developing-your-own-helper-function"></a>開發您自己的 Helper 函式
若要提供您自己進行匯入之 DLL 的名稱為基礎的特定處理常式的版本。 這麼做的兩種方法： 程式碼撰寫您自己，可能會根據提供的程式碼，或攔截所提供的版本，使用先前說明的告知攔截。  
  
 程式碼自己  
 這是相當簡單，因為您實際上可以使用當做指導方針提供的程式碼，新的。 當然，它必須遵守的呼叫慣例，而且如果它傳回至連結器產生的 thunk，它必須傳回適當的函式指標。 一次在您的程式碼中，您可以執行幾乎任何您想要以滿足呼叫或者跳離呼叫。  
  
 使用啟動處理告知攔截  
 它可能會直接提供新的指標，以接收通知 dliStartProcessing 上預設協助專家為相同值的使用者提供的通知攔截函式最簡單的方式。 此時，攔截函式基本上會形成新的協助程式函式，是因為成功傳回預設協助程式將會略過所有其他以預設協助程式處理。  
  
## <a name="see-also"></a>另請參閱  
 [延遲載入 DLL 的連結器支援](../../build/reference/linker-support-for-delay-loaded-dlls.md)