---
{"dg-publish":true,"permalink":"/content/df/soap-making/","title":"Soap Making","tags":["DwarfFortress"]}
---

> [!tldr] 
> Soap is dwarven happiness juice that fights dirt and infection. Make it from wood and fat, then let your dwarves take soapy baths to boost morale. Also useful for hospitals and emergency soap walls!

> [!summary] 
> Soap is crucial for dwarven health and happiness, preventing infections and boosting moods. It’s made from lye (produced from wood ash) and fat (tallow or oil). The production process involves chopping wood, making ash, producing lye, and rendering fat or pressing oil. Use soap for baths and in hospitals to reduce infection risk. Dwarves clean up with or without it, but a soapy bath makes them happier. Store soap in bar/block stockpiles and build emergency soap walls to keep reserves handy.

# Diagram
Below is a diagram of how to setup a Soap Making Industry in Dwarf Fortress
There are 3 Paths to choose from:
1. Path of Lye
2. Path of Tallow
3. Path of Oil
Each path have some boxes and ind these boxes there are requirements and actions that needs some of the requirements to be activated.
*Example of an action*
`Action Name`(`requirement`) : `Output`

*Example of a requirement*
`Requirement Name` :  `Type`
```plantuml

!if %not(%variable_exists("$BGCOLOR"))
!$BGCOLOR = "#282a36"
!endif

'Colors
!$Background 	= 	'#282a36'
!$CurrentLine 	= 	'#44475a'
!$Foreground 	= 	'#f8f8f2'
!$Comment 		= 	'#6272a4'
!$Cyan 			= 	'#8be9fd'
!$Green 		= 	'#50fa7b'
!$Orange 		= 	'#ffb86c'
!$Pink 			= 	'#ff79c6'
!$Purple 		= 	'#bd93f9'
!$Red 			= 	'#ff5555'
!$Yellow 		= 	'#f1fa8c'

skinparam BackgroundColor $Background 
 ' ____                         _                     
 '|  _ \ _ __ ___   ___ ___  __| |_   _ _ __ ___  ___ 
 '| |_) | '__/ _ \ / __/ _ \/ _` | | | | '__/ _ \/ __|
 '|  __/| | | (_) | (_|  __/ (_| | |_| | | |  __/\__ \
 '|_|   |_|  \___/ \___\___|\__,_|\__,_|_|  \___||___/
                                                     

'  ___ _     _    _                                    
' | __(_)___| |__| | 
' | _|| / -_) / _` | 
' |_| |_\___|_\__,_| 
                                                       
!unquoted procedure $Property($AccessModifier, $Restriction, $Name, $Type)
!if ($Restriction!="")
$AccessModifier <color:$Orange>$Restriction</color> <color:$Foreground>$Name</color> : <color:$Purple>$Type</color>
!else
$AccessModifier  <color:$Foreground>$Name</color> : <color:$Purple>$Type</color>
!endif
!endprocedure

'  __  __     _   _            _                    
' |  \/  |___| |_| |_  ___  __| | 
' | |\/| / -_)  _| ' \/ _ \/ _` | 
' |_|  |_\___|\__|_||_\___/\__,_|  
                                                                           
!unquoted procedure $Method($AccessModifier, $MethodName, $Parameter, $ReturnValue)
!if ($ReturnValue != "")
$AccessModifier <color:$Pink>$MethodName(<color:$Foreground>$Parameter</color><color:$Pink>)</color><color:$Foreground> : </color><color:#f1fa8c>$ReturnValue</color>
!else
$AccessModifier <color:$Pink>$MethodName(<color:$Foreground>$Parameter</color><color:$Pink>)</color> 
!endif
!endprocedure

'   ___             _               _            
'  / __|___ _ _  __| |_ _ _ _  _ __| |_ ___ _ _  
' | (__/ _ \ ' \(_-<  _| '_| || / _|  _/ _ \ '_| 
'  \___\___/_||_/__/\__|_|  \_,_\__|\__\___/_| 
!unquoted procedure $Constructor($AccessModifier, $MethodName, $Parameter)
$AccessModifier <color:$Pink>$MethodName(<color:$Foreground>$Parameter</color><color:$Pink>)</color>
!endprocedure

'  ___     _      _   _             
' | _ \___| |__ _| |_(_)___ _ _  ___
' |   / -_) / _` |  _| / _ \ ' \(_-<
' |_|_\___|_\__,_|\__|_\___/_||_/__/
                                   
!unquoted procedure $InherritsFromAbstraction($Concrete,$Abstraction)
$Concrete ..|> $Abstraction
!endprocedure

!unquoted procedure $InherritsFromConcrete($ObjectA,$ObjectB)
$ObjectA --|> $ObjectB
!endprocedure

!unquoted procedure $ObjectAssociation($ObjectA,$ObjectB)
$ObjectA -- $ObjectB
!endprocedure

!unquoted procedure $ObjectDependency($ObjectA,$ObjectB)
$ObjectA ..> $ObjectB
!endprocedure

!unquoted procedure $ObjectComposition($ObjectA,$ObjectB)
$ObjectA *-- $ObjectB
!endprocedure

!unquoted procedure $ObjectAggregation($ObjectA,$ObjectB)
$ObjectA o-- $ObjectB
!endprocedure

'  ___ ___ ___  _   _ ___ _  _  ___ ___   ___ ___   _   ___ ___    _   __  __  
' / __| __/ _ \| | | | __| \| |/ __| __| |   \_ _| /_\ / __| _ \  /_\ |  \/  | 
' \__ \ _| (_) | |_| | _|| .` | (__| _|  | |) | | / _ \ (_ |   / / _ \| |\/| | 
' |___/___\__\_\\___/|___|_|\_|\___|___| |___/___/_/ \_\___|_|_\/_/ \_\_|  |_| 
!unquoted procedure $Message($SMSObjectA, $SMSObjectB, $SMSMethod, $SMS_Parameters)
!if ($SMSMethod!="")
$SMSObjectA -[$Orange]> $SMSObjectB : <color:$Pink>$SMSMethod(</color><color:$Foreground>$SMS_Parameters</color><color:$Pink>)</color>
!else
$SMSObjectA -[$Orange]> $SMSObjectB 
!endif
!endprocedure

!unquoted procedure $SynchronousReturnMessage($SMSObjectA, $SMSObjectB, $SMSMethod, $SMS_Parameters)
$SMSObjectA <[$Orange]- $SMSObjectB : <color:$Pink>$SMSMethod(</color><color:$Foreground>$SMS_Parameters</color><color:$Pink>)</color>
!endprocedure

!unquoted procedure $ASynchronousMessage($AMSObjectA, $AMSObjectB, $AMSMethod, $AMS_Parameters)
$AMSObjectA -[$Orange]->> $AMSObjectB : <color:$Pink>$AMSMethod(</color><color:$Foreground>$AMS_Parameters</color><color:$Pink>)</color>
!endprocedure

!unquoted procedure $ReturnMessage($AMSObjectA, $AMSObjectB, $AMSMethod, $AMS_Parameters)
$AMSObjectA <-[$Orange]- $AMSObjectB : <color:$Pink>$AMSMethod(</color><color:$Foreground>$AMS_Parameters</color><color:$Pink>)</color>
!endprocedure

!unquoted procedure $PlainMessage($AMSObjectA, $AMSObjectB, $AMSMessage,)
$AMSObjectA -[$Orange]> $AMSObjectB : <color:$Yellow>$AMSMessage</color>
!endprocedure
!unquoted procedure $PlainReturnMessage($AMSObjectA, $AMSObjectB, $AMSMessage,)
$AMSObjectA <-[$Orange]- $AMSObjectB : <color:$Yellow>$AMSMessage</color>
!endprocedure


skinparam defaultFontName       "IBM Plex Sans, Noto Sans, Verdana"
skinparam defaultFontSize       12
skinparam shadowing             false
skinparam roundcorner           0
skinparam ParticipantPadding    30
skinparam BoxPadding            30
skinparam Padding               2
skinparam nodesep               30
skinparam ranksep               100
skinparam dpi                   300

skinparam title {
	FontColor	                 $Foreground
	BorderColor	                 $Foreground
	FontSize	    	         20
	BorderRoundCorner            8
	BorderThickness 	         0
	BackgroundColor              $BGCOLOR
}
skinparam legend {
	BackgroundColor         	$Background
	BorderColor             	$Red
	FontColor               	$Foreground
	BorderThickness				3
}

!startsub arrow
skinparam arrow {
	Thickness               	3
	Color                   	$Cyan
	FontColor               	$Green
}
!endsub


!startsub note
skinparam note {
	BorderThickness         	1
	BackgroundColor         	$Green
	BorderColor             	$Green
	FontColor               	$Background
	RoundCorner             	0
}
!endsub

!startsub class
skinparam Class {
    'skinparam ClassHeaderBackgroundColor $Purple
	HeaderBackgroundColor   	$Purple
	StereotypeFontColor     	$Foreground
	StereotypeFontSize      	9
	BorderThickness         	2
    BorderColor             	$Purple
    FontSize                	16
	AttributeFontColor      	$Foreground
	AttributeFontSize       	11
    AttributeIconSize       	10
    BackgroundColor         	$CurrentLine
    FontColor               	$Foreground
    StereotypeFontColor     	$Orange 
}
!endsub

!startsub interface

skinparam interface {
	BackgroundColor  			$Background
	BorderColor  				$Purple
	FontColor			 		$Foreground
}
!endsub

!startsub component
skinparam component {
	BackgroundColor         	$CurrentLine
	BorderColor             	$Foreground
    BorderThickness         	0
}
!endsub

!startsub sequence
skinparam sequence {
	BorderColor 				$Red
	' For some reason sequence title font color does not pick up from global
	TitleFontColor 				$Orange
	BackgroundColor 			$Background 
	StartColor 					$Foregound
	EndColor 					$Foreground
	''
	BoxBackgroundColor 			$CurrentLine
	BoxBorderColor 				$CurrentLine
	BoxFontColor 				$Background
	' ''
	DelayFontColor 				$Orange
	''
	LifeLineBorderColor 		$Foreground
	BorderThickness 			2
	LifeLineBackgroundColor 	$Foreground
	' ''
	GroupBorderColor 			$Red
	GroupFontColor 				$Red
	GroupFontStyle 				bold
	GroupHeaderFontColor 		$Background
	GroupBackgroundColor 		$Red 
    GroupBodyBackgroundColor 	#Transparent
	GroupHeaderBackgroundColor 	$Red
    GroupBorderThickness 		1
	' ''
	DividerBackgroundColor 		$Orange
    DividerBorderColor 			$Orange
    DividerBorderThickness 		2
    DividerFontColor 			$CurrentLine
	' ''
	ReferenceBackgroundColor 	$Comment
	ReferenceHeaderBorderColor 	$Yellow
	ReferenceHeaderBackgroundColor $Yellow
	ReferenceBorderColor 		$Comment
	ReferenceFontColor 			$Background
	ReferenceHeaderFontColor 	$Foreground
	' ''
	StereotypeFontColor 		$Foreground
    
}
!endsub
skinparam Style strictUML

!startsub participant
skinparam participant {
	ParticipantBorderThickness 	3
    BackgroundColor 			$Orange 
    BorderColor 				$Orange 
}
!endsub
!startsub package
skinparam package {
	BackgroundColor         	$Background
	BorderThickness         	3
    FontColor               	$Foreground 
    StereotypeFontColor     	$Foreground 
    BorderColor             	$Red
}
!endsub
!startsub rectangle
skinparam rectangle {
    FontColor               	$Foreground
    FontSize                	16
	BackgroundColor         	$Background
	BorderThickness         	2
    BorderColor             	$Red
	StereotypeFontColor     	$Foreground
}
!endsub
!startsub actor
skinparam actor {
	BackgroundColor     		$Orange 
    BorderThickness     		3
    BorderColor         		$Orange
    FontColor           		$Orange 
}
!endsub

!startsub database
skinparam database {
	BorderColor         		$Background
	BackgroundColor     		$Orange
	Roundcorner         		0
}
!endsub

!startsub folder

skinparam folder {
	BackgroundColor 			$CurrentLine
  	BorderColor 				$Purple
	FontColor 					$Foreground
	BorderThickness 			3
	Roundcorner 				0
}
!endsub

!startsub frame

skinparam frame {
	BackgroundColor 			$CurrentLine
  	BorderColor 				$Purple
	FontColor 					$Foreground
	BorderThickness 			3
	Roundcorner 				0
}
!endsub

' state here


!startsub card

skinparam card {
	BackgroundColor 			$CurrentLine
	BorderColor 				$Purple
	FontColor 					$Foreground
	RoundCorner 				0
}
!endsub

!startsub file

skinparam file {
	BackgroundColor 			$CurrentLine
	BorderColor 				$Purple
	FontColor 					$Foreground
	RoundCorner 				0

}
!endsub

!startsub gantt

!endsub
package "Path of Lye" as PathLye{
	class "Wood" as Wood{
	-- Requirements --
	$Property(+,,Dwarf, Any)
	$Property(+,,BattleAxe, Any)
	-- Actions --
	$Method(,Log, ,Wood)
	}
	class "Wood Furnace" as WoodFurnace{
	-- Requirements --
	$Property(+,,Wood,Any)
	-- Actions --
	$Method(,Burn, Wood, Ash)
	}
	class "Ashery" as Ashery{
	-- Requirements --
	$Property(+,,Ash,Bar)
	-- Actions --
	$Method(,MakeLye,Ash,Lye)
	}

}
package "Path of Tallow" as PathTallow{
	class "Butcher" as Butcher{
	-- Requirements --
	$Property(+,,Dwarf, Any)
	$Property(+,,Animal, Any)
	-- Actions --
	$Method(,Butcher, ,Fat)
	}
	class "Kitchen" as Kitchen{
	-- Requirements --
	$Property(+,,Fat,Any)
	-- Actions --
	$Method(,RenderFat, Fat, Tallow)
	}
	

}
package "Path of Oil" as PathOil{
	class "Quern" as Quern{
	-- Requirements --
	$Property(+,,Dwarf, Any)
	$Property(+,,Seeds, Oily)
	-- Actions --
	$Method(,MillSeeds,Seeds,Paste)
	}
	class "Screw Press" as ScrewPress{
	-- Requirements --
	$Property(+,,Paste,Any)
	-- Actions --
	$Method(,PressOil, Paste, Oil)
	}
	

}
class "Soap Maker's Workshop" as Soap{
-- Requirements --
$Property(+,,Oil, Any)
$Property(+,,Tallow, Any)
$Property(+,,Lye, Any)
-- Actions --
$Method(,MakeSoap, Lye; Oil or Tallow, Soap)

}
$InherritsFromConcrete(Wood,WoodFurnace)
$InherritsFromConcrete(WoodFurnace, Ashery)
$InherritsFromConcrete(Butcher,Kitchen)
$InherritsFromConcrete(Kitchen,Soap)
$InherritsFromConcrete(Ashery, Soap)
$InherritsFromConcrete(Quern, ScrewPress)
$InherritsFromConcrete(ScrewPress, Soap)
```


# Sources

| Source                                                                       | Description                         |
| ---------------------------------------------------------------------------- | ----------------------------------- |
| [Wiki - Dwarf Fortress](https://dwarffortresswiki.org/index.php/DF2014:Soap) | Wikipedia article about soap making |


