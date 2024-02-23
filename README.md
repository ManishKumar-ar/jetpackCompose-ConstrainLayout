this is the constraint layout brief 

Constraint Layout is not present in the jetpack compose by default.
we have to add a dependency -
                             implementation ("androidx.constraintlayout:constraintlayout-compose:1.0.1")

we directly not use the constaint layout 
step 1  - 
we have to define the contraint set, which define our layout in the screen.


step - 2
we define our contrains in the ConstraintSet{}

val constraints  = ConstraintSet { }

ConstraintLayout: Use the ConstraintLayout composable to create a ConstraintLayout.
Inside this composable, you'll define your child composables and specify constraints between them.

ConstraintSet: Use the ConstraintSet class to define constraints between the child composables.
You can create multiple instances of ConstraintSet to represent different states/layouts of your UI.


step - 3
 val constraints  = ConstraintSet {
                val greenBox =createRefFor("greenbox")
                val redBox =createRefFor("redbox")
   }

   here createRefFor are the predefined function in the constraintset and in the constraintset, we define our child composable and wehave to give an id --
   by using the createRefFor()



  step -4
   in Jetpack Compose, "constrain" refers to the process of specifying the positioning and alignment rules for child composables within 
   the layout. When you apply constraints to a composable, you are defining how it should be positioned relative to other composables or to the parent layout.

Constraints typically include rules like aligning the top, bottom, start (left), or end (right) edges of a composable to another composable or to the edges of the parent layout.
These constraints help define the layout's structure and how its elements are arranged on the screen.



top.linkTo(), bottom.linkTo(), start.linkTo(), end.linkTo(), etc., to specify the desired relationships between the composables.

     val constraints  = ConstraintSet {
                val greenBox =createRefFor("greenbox")
                val redBox =createRefFor("redbox")

                constrain(greenBox){
                    top.linkTo(parent.top)
                    start.linkTo(parent.start)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                constrain(redBox){
                    top.linkTo(parent.top)
                    start.linkTo(greenBox.end)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }

            }




step - 5
 ConstraintLayout (constraints, modifier= Modifier.fillMaxSize())
 {
                
    }

here we use the constraint layout and in this we use our constraints that we made in the earlier by using their id's  - layoutID

 ConstraintLayout (constraints, modifier= Modifier.fillMaxSize())
 {

                Box(modifier = Modifier
                    .background(Color.Green)
                    .layoutId("greenbox")                              // here we tell the box that hey- you are the green that we desig your layout 
                )
                Box(modifier = Modifier
                    .background(Color.Red)
                    .layoutId("redbox")
                )
            }



step - 6
setContent {
            val constraints  = ConstraintSet {
                val greenBox = createRefFor("greenbox")
                val redBox = createRefFor("redbox")
                val blueBox = createRefFor("bluebox")
                val blackBox = createRefFor("blackbox")


                constrain(greenBox){
                    top.linkTo(parent.top)
                    start.linkTo(parent.start)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                constrain(redBox){
                    top.linkTo(parent.top)
                    start.linkTo(greenBox.end)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                constrain(blackBox){
                    top.linkTo(parent.top)
                    start.linkTo(redBox.end)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }
                constrain(blueBox){
                    top.linkTo(parent.top)
                    start.linkTo(blackBox.end)
                    width = Dimension.value(100.dp)
                    height = Dimension.value(100.dp)
                }

            }

            ConstraintLayout (constraints, modifier= Modifier.fillMaxSize()){

                Box(modifier = Modifier
                    .background(Color.Green)
                    .layoutId("greenbox")
                )
                Box(modifier = Modifier
                    .background(Color.Red)
                    .layoutId("redbox")
                )
                Box(modifier = Modifier
                    .background(Color.Blue)
                    .layoutId("bluebox")
                )
                Box(modifier = Modifier
                    .background(Color.Cyan)
                    .layoutId("blackbox")
                )
            }

        }

        









   
