---
title: SpriteKit in xamarin. IOS
description: Questo documento descrive SpriteKit, framework grafica 2D di Apple che si integra con SceneKit, incorpora fisica e animazione, include il supporto di illuminazione e dello sfondo e altro ancora. SpriteKit può essere utilizzato per creare giochi 2D.
ms.prod: xamarin
ms.assetid: 93971DAE-ED6B-48A8-8E61-15C0C79786BB
ms.technology: xamarin-ios
author: bradumbaugh
ms.author: brumbaug
ms.date: 06/14/2017
ms.openlocfilehash: b74b5a722aab240b55ed96bea2a33b162d7817eb
ms.sourcegitcommit: ea1dc12a3c2d7322f234997daacbfdb6ad542507
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/05/2018
ms.locfileid: "34786769"
---
# <a name="spritekit-in-xamarinios"></a>SpriteKit in xamarin. IOS

SpriteKit, il framework di grafica 2D di Apple, include alcune nuove funzionalità interessanti in iOS 8 e OS X Yosemite. Queste includono l'integrazione con SceneKit, supporto dello shader, illuminazione, ombreggiature, vincoli, la generazione di mappe normali e miglioramenti fisica. In particolare, le nuove funzionalità di fisica rendono molto semplice aggiungere effetti realistici per un gioco.

## <a name="physics-bodies"></a>Corpi fisica

SpriteKit include un 2D, fisica corpo rigida API. Ogni sprite ha un corpo fisica associato (`SKPhysicsBody`) che definisce le proprietà fisiche, ad esempio massa le forze di attrito, nonché la geometria del corpo nel mondo fisica.

## <a name="creating-a-physics-body-from-a-texture"></a>Creazione di un corpo fisica da una trama
SpriteKit supporta ora la derivazione corpo fisica di un sprite la trama. Questo rende facile da implementare conflitti che più naturali.

Ad esempio, si noti che nel conflitto seguente come le banana monkey sono in conflitto quasi alla superficie di ogni immagine:
 
![](spritekit-images/image13.png "Sono in conflitto di banana e monkey quasi alla superficie di ogni immagine")

SpriteKit permette la creazione di questo tipo un corpo di fisica con una singola riga di codice. È sufficiente chiamare `SKPhysicsBody.Create` con la trama e le dimensioni: sprite. PhysicsBody = SKPhysicsBody.Create (sprite. Trama, sprite. Dimensioni).

## <a name="alpha-threshold"></a>Soglia alpha

Oltre a impostare semplicemente il `PhysicsBody` proprietà direttamente alla geometria derivata dalla trama, le applicazioni possono impostare la soglia alpha per controllare come verrà derivata la geometria e. 

La soglia alpha definisce il valore alfa minimo di che un pixel deve disporre per essere incluso nel corpo della fisica risultante. Ad esempio, il codice seguente comporta un corpo fisica leggermente diverso:

```chsarp
sprite.PhysicsBody = SKPhysicsBody.Create (sprite.Texture, 0.7f, sprite.Size);
```

L'effetto dell'ottimizzazione la soglia alpha simile al seguente ottimizza il conflitto precedente, in modo che il monkey rientra quando è in conflitto con il banana:

![](spritekit-images/image14.png "Il monkey rientra quando è in conflitto con il banana")
 
## <a name="physics-fields"></a>Campi fisica

Un'altra aggiunta importante per SpriteKit è supportano il nuovo campo fisica. Questi consentono di aggiungere, ad esempio, i campi vortex, gravità radiale campi e i campi di primavera per assegnare un nome di un numero limitato.

Campi fisica vengono creati utilizzando la classe SKFieldNode, che viene aggiunto a una scena come qualsiasi altro `SKNode`. Esistono diversi metodi factory per `SKFieldNode` per creare campi fisica diversa. È possibile creare un campo spring chiamando `SKFieldNode.CreateSpringField()`, un campo della radiale gravità chiamando `SKFieldNode.CreateRadialGravityField()`e così via.

`SKFieldNode` dispone anche di controllare gli attributi di campo, ad esempio il livello di campo, l'area di campo e l'attenuazione di forza di campo.

## <a name="spring-field"></a>Campo molla

Ad esempio, il codice seguente crea un campo molla e lo aggiunge alla scena:

```csharp
SKFieldNode fieldNode = SKFieldNode.CreateSpringField ();
fieldNode.Enabled = true;
fieldNode.Position = new PointF (Size.Width / 2, Size.Height / 2);
fieldNode.Strength = 0.5f;
fieldNode.Region = new SKRegion(Frame.Size);
AddChild (fieldNode);
```

È quindi possibile aggiungere Sprite e impostare i relativi `PhysicsBody` proprietà in modo che il campo fisica influisce Sprite, in quanto il codice seguente esegue quando l'utente tocca lo schermo:

```csharp
public override void TouchesBegan (NSSet touches, UIEvent evt)
{
    var touch = touches.AnyObject as UITouch;
    var pt = touch.LocationInNode (this);
    var node = SKSpriteNode.FromImageNamed ("TinyBanana");
    node.PhysicsBody = SKPhysicsBody.Create (node.Texture, node.Size);
    node.PhysicsBody.AffectedByGravity = false;
    node.PhysicsBody.AllowsRotation = true;
    node.PhysicsBody.Mass = 0.03f;
    node.Position = pt;
    AddChild (node);
}
```

In questo modo le banane in oscillazione come una molla intorno al nodo di campo:

![](spritekit-images/image15.png "Banane oscillazione come una molla intorno al nodo di campo")
 
## <a name="radial-gravity-field"></a>Campo gravità radiale

Aggiunta di un campo diverso è simile. Ad esempio, il codice seguente crea un campo della radiale gravità:

```csharp
SKFieldNode fieldNode = SKFieldNode.CreateRadialGravityField ();
fieldNode.Enabled = true;
fieldNode.Position = new PointF (Size.Width / 2, Size.Height / 2);
fieldNode.Strength = 10.0f;
fieldNode.Falloff = 1.0f;
```

Ciò comporta un altro campo force, in cui banane vengono estratti in modo radiale sul campo:

![](spritekit-images/image16.png "Banane vengono estratti in modo radiale attorno al campo")
