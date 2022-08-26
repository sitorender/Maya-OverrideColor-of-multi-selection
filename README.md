// Maya-OverrideColor-of-multi-selection
// Script to change Override Color of all the selected objects



string $text;
int $ovecolor[];
string $result = `promptDialog
    -title "Rename Object"
    -message "Enter Name:"
    -button "OK" -button "Cancel"
    -defaultButton "OK" -cancelButton "Cancel"
    -dismissString "Cancel"`;

if ($result == "OK") {
    $text = `promptDialog -query -text`;
    $ovecolor[0] = $text;

}
 string $sel[] = `ls -sl`;
 string $shNoden[];
 
 for($x=0;$x<size($sel);$x++)
 {
 	select -r $sel[$x];
 	$shNoden = `pickWalk -d down`;
 	setAttr($shNoden[0] + ".overrideEnabled")1;
 	setAttr($shNoden[0] + ".overrideColor")$ovecolor[0];
 };

 select -cl;
