---
title: "/Zc:sizedDealloc （啟用全域調整大小解除配置函式） |Microsoft 文件"
ms.custom: 
ms.date: 12/13/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1343c037f87aee609de2b082cb87f7f1f2832221
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc:sizedDealloc （啟用全域調整大小解除配置函式）  
`/Zc:sizedDealloc`編譯器選項會告訴編譯器優先呼叫全域`operator delete`或`operator delete[]`函式具有類型的第二個參數的`size_t`時可用的物件大小。 這些函式可能會使用`size_t`參數來最佳化效能的解除配置器。   
  
## <a name="syntax"></a>語法  
`/Zc:sizedDealloc`[`-`\]  
  
## <a name="remarks"></a>備註  
  
C + + 11 標準，您可以定義靜態成員函式`operator delete`和`operator delete[]`，花一些時間，`size_t`參數。 通常搭配使用這些[運算子 new](../../cpp/new-operator-cpp.md)函式以實作更有效率的配置器和解除配置器物件。 不過，C + + 11 未定義在全域範圍的解除配置函式的對等設定。 在 C + + 11、 全域解除配置函式具有類型的第二個參數的`size_t`會被視為 placement delete 函式。 他們必須藉由傳遞大小引數明確呼叫。  
  
C + + 14 標準變更編譯器的行為。 當您定義全域`operator delete`和`operator delete[]`可接受類型的第二個參數`size_t`，編譯器慣用時要呼叫這些函式不會叫用成員範圍版本和物件的大小。 編譯器會以隱含方式傳遞的大小引數。 當編譯器無法判斷已解除配置物件的大小，會呼叫單一引數版本。 否則，選擇要叫用的解除配置函式版本的一般規則仍然套用。 呼叫全域函式可明確指定附加在前面的範圍解析運算子 (`::`) 的解除配置函式呼叫。  
  
根據預設，啟動 Visual Studio 2015 中的 Visual c + + 實作此 C + + 14 標準行為。 您可能會明確指定這項設定`/Zc:sizedDealloc`編譯器選項。 這表示可能最新變更。 使用`/Zc:sizedDealloc-`選項，可保留舊的行為，例如，當您的程式碼會定義使用類型的第二個參數的位置刪除運算子`size_t`。 具有第二個參數類型的全域解除配置函式的預設 Visual Studio 程式庫實作`size_t`叫用的單一參數的版本。 如果您的程式碼提供只有單一參數全域 delete 運算子和 delete 運算子 []，全域調整大小解除配置函式的預設程式庫實作叫用全域函式。  
  
如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
2.  從**組態**下拉式功能表中，選擇 **所有組態**。  
3.  選取**組態屬性**， **C/c + +**，**命令列**屬性頁。  
4.  修改**其他選項**屬性，以包括`/Zc:sizedDealloc`或`/Zc:sizedDealloc-`，然後選擇 **確定**。  
  
## <a name="see-also"></a>請參閱  
[編譯器選項](../../build/reference/compiler-options.md)  
[設定編譯器選項](../../build/reference/setting-compiler-options.md)  
[/Zc （一致性）](../../build/reference/zc-conformance.md)  
