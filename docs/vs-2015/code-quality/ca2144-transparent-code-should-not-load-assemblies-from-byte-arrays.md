---
title: 'CA2144: прозрачный код не должен загружать сборки из массивов байтов | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2144
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 36b27880b5574e9e47067c240bc162cc15e8d3b6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610321"
---
# <a name="ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays"></a>CA2144: прозрачный код не должен загружать сборки из массивов байтов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|транспарентмесодсшаулднотлоадассемблиесфромбитеаррайс|
|CheckId|CA2144|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод загружает сборку из массива байтов с помощью одного из следующих методов:

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

- <xref:System.Reflection.Assembly.Load%2A>

## <a name="rule-description"></a>Описание правила
 Проверка безопасности для прозрачного кода не так тщательна, как проверка безопасности для критического кода, поскольку прозрачный код не может выполнять действия, требующие особых мер безопасности. Сборки, загруженные из массива байтов, могут остаться незамеченными в прозрачном коде, и этот массив байтов может содержать критичный или, что более важно, критичный в плане безопасности код, который подлежит аудиту. Таким образом, прозрачный код не должен загружать сборки из массива байтов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, пометьте метод, загружающий сборку, с помощью <xref:System.Security.SecurityCriticalAttribute> или атрибута <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Правило срабатывает для следующего кода, поскольку прозрачный метод загружает сборку из массива байтов.

 [!code-csharp[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2144.transparentmethodsshouldnotloadassembliesfrombytearrays/cs/ca2144 - transparentmethodsshouldnotloadassembliesfrombytearrays.cs#1)]
