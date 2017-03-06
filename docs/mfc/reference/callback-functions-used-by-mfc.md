---
title: "MFC 使用的回呼函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions, MFC
- MFC, callback functions
- functions [C++], callback
- callback functions
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: b4d104fa76347da43c84611672f843511f0f3725
ms.lasthandoff: 02/24/2017

---
# <a name="callback-functions-used-by-mfc"></a>MFC 使用的回呼函式
三個回呼函式會出現在 Mfc 程式庫。 傳遞至回呼函式的說明[cdc:: enumobjects](../../mfc/reference/cdc-class.md#enumobjects)， [cdc:: graystring](../../mfc/reference/cdc-class.md#graystring)，和[cdc:: setabortproc](../../mfc/reference/cdc-class.md#setabortproc)遵循本主題。 回呼函式的一般用法，請參閱這些成員函式的 < 備註 > 一節。 請注意，所有的回呼函式必須捕捉 MFC 例外狀況，然後再回到 Windows 中，因為無法跨越界限回呼擲回例外狀況。 如需例外狀況的詳細資訊，請參閱文章[例外狀況](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="see-also"></a>另請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


