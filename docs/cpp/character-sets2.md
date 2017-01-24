---
title: "字元集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
helpviewer_keywords: 
  - "字元集"
  - "基本來源字元集 (C++)"
  - "通用字元名稱"
  - "基本執行字元集 (C++)"
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 字元集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 程式的文字會儲存在使用特定字元編碼方式的原始程式檔中。 C\+\+ 標準指定原始程式檔的基本來源字元集，以及編譯檔的基本執行字元集。 Visual C\+\+ 允許在原始程式檔和編譯檔中使用一組額外的地區設定特定字元。  
  
## 字元集  
 C\+\+ 標準指定可用於原始程式檔的*「基本來源字元集」*\(Basic Source Character Set\)。 為了表示不在這個集合中的字元，還可使用*「通用字元名稱」*\(Universal Character Name\) 來指定額外的字元。 編譯時，*「基本執行字元集」*\(Basic Execution Character Set\) 和*「基本執行寬字元集」*\(Basic Execution Wide\-Character Set\) 會代表可出現在程式中的字元和字串。 Visual C\+\+ 實作允許在原始程式碼和編譯程式碼中使用額外的字元。  
  
### 基本來源字元集  
 *「基本來源字元集」*\(Basic Source Character Set\) 是由可用於原始程式檔的 96 個字元所組成。 這個集合包含空白字元、水平定位字元、垂直定位字元、換頁字元和換行控制字元，以及下列一組圖形字元：  
  
 `a b c d e f g h i j k l m n o p q r s t u v w x y z`  
  
 `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`  
  
 `0 1 2 3 4 5 6 7 8 9`  
  
 `_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`  
  
 **Microsoft 特定的**  
  
 Visual C\+\+ 包含 `$` 字元做為基本來源字元集的成員。 根據檔案編碼方式，Visual C\+\+ 也允許在原始程式檔中使用一組額外的字元。 根據預設，Visual Studio 會使用預設字碼頁來儲存原始程式檔。 當使用地區設定特定字碼頁或 Unicode 字碼頁來儲存原始程式檔時，Visual C\+\+ 可讓您在原始程式碼中使用該字碼頁的任何字元，但不包括基本來源字元集中未明確允許的控制碼。 例如，如果您使用日文字碼頁來儲存檔案，則可以將日文字元放在註解、識別項或字串常值中。 Visual C\+\+ 不允許無法轉譯為有效的多位元組字元或 Unicode 字碼指標的字元序列。 根據編譯器選項，並非所有允許的字元都可出現在識別項中。 如需詳細資訊，請參閱[C\+\+ 識別項](../cpp/identifiers-cpp.md)。  
  
 **END Microsoft 特定的**  
  
### 通用字元名稱  
 由於 C\+\+ 程式可以使用比基本來源字元集所指定的字元還要多的字元，因此您可以使用*「通用字元名稱」*\(Universal Character Name\)，透過移植的方式來指定這些字元。 通用字元名稱是由代表 Unicode 字碼指標的字元序列所組成。  這些字元採用兩種格式。 使用 `\UNNNNNNNN` 來表示 U\+NNNNNNNN 格式的 Unicode 字碼指標，其中 NNNNNNNN 是八位數的十六進位字碼指標數字。 使用四位數的 `\uNNNN` 來表示 U\+0000NNNN 格式的 Unicode 字碼指標。  
  
 通用字元名稱可用於識別項、字串和字元常值中。 通用字元名稱不可用來代表範圍 0xD800\-0xDFFF 中的 Surrogate 字碼指標。 請改用想要的字碼指標；編譯器會自動產生任何必要的 Surrogate。 可用於識別項的通用字元名稱還有其他限制。 如需詳細資訊，請參閱[C\+\+ 識別項](../cpp/identifiers-cpp.md) 和[字串和字元常值](../cpp/string-and-character-literals-cpp.md)。  
  
 **Microsoft 特定的**  
  
 Visual C\+\+ 編譯器會將通用字元名稱格式的字元，視為可以與常值格式的字元交換使用。 例如，您可以使用通用字元名稱格式宣告一個識別項，然後以常值格式來使用該識別項：  
  
```cpp  
auto \u30AD = 42; // \u30AD is 'キ' if (キ == 42) return true; // \u30AD and キ are the same to the compiler  
  
```  
  
 Windows \[剪貼簿\] 上的擴充字元格式會因應用程式地區設定而有所不同。 將這些字元從另一個應用程式剪下並貼到您的程式碼可能會採用未預期的字元編碼方式。 這會導致程式碼中出現沒有明顯原因的剖析錯誤。 建議您先將原始程式檔編碼方式設定為 Unicode 字碼頁，再剖析擴充字元。 此外，也建議您使用 IME 或字元對應表應用程式來產生擴充字元。  
  
 **END Microsoft 特定的**  
  
### 基本執行字元集  
 *「基本執行字元集」*\(Basic Execution Character Set\) 和*「基本執行寬字元集」*\(Basic Execution Wide\-Character Set\) 包含基本來源字元集中的所有字元，以及代表警示、Backspace、歸位字元和 null 字元的控制字元。*「執行字元集」*\(Execution Character Set\) 和*「執行寬字元集」*\(Execution Wide\-Character Set\) 是基本集合的超集。 這些超集包含基本來源字元集以外已定義實作的來源字元。 執行字元集具有地區設定特定表示法。