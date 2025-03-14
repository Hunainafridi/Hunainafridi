import 'package:flutter/material.dart';

 

void main() {

runApp(MyMagicApp()); 

}

 

class MyMagicApp extends StatelessWidget {

@override 

Widget build(BuildContext context) { 

  return MaterialApp(

    debugShowCheckedModeBanner: false,

    home: MagicHomePage(),

  );

}

}

 

class MagicHomePage extends StatefulWidget {

@override 

_MagicHomePageState createState() => _MagicHomePageState(); 

}

 

class _MagicHomePageState extends State<MagicHomePage> {

int _selectedIndex = 0; 

TextEditingController _controller = TextEditingController(); 

 

List<String> items = ["Apple", "Banana", "Cherry", "Mango", "Grapes"]; 

 

void _onItemTapped(int index) { 

  setState(() {

    _selectedIndex = index;

  });

}

 

@override 

Widget build(BuildContext context) { 

  return Scaffold(

    appBar: AppBar(

      title: Text('Magic App'),

      backgroundColor: Colors.blueAccent,

    ),

    body: Padding(

      padding: EdgeInsets.all(16.0),

      child: Column(

        children: [

          TextField(

            controller: _controller,

            decoration: InputDecoration(

              labelText: "Enter your name",

              border: OutlineInputBorder(),

            ),

          ),

          SizedBox(height: 10),

          ElevatedButton(

            onPressed: () {

              showDialog(

                context: context,

                builder: (context) => AlertDialog(

                  title: Text("Hello, ${_controller.text}!"),

                ),

              );

            },

            child: Text("Click Me!"),

          ),

          Expanded(

            child: GridView.builder(

              gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(

                crossAxisCount: 2,

                childAspectRatio: 2,

                crossAxisSpacing: 10,

                mainAxisSpacing: 10,

              ),

              itemCount: items.length,

              itemBuilder: (context, index) {

                return Card(

                  color: Colors.amberAccent,

                  child: Center(child: Text(items[index])),

                );

              },

            ),

          ),

        ],

      ),

    ),

    bottomNavigationBar: BottomNavigationBar(

      items: const <BottomNavigationBarItem>[

        BottomNavigationBarItem(

          icon: Icon(Icons.home),

          label: 'Home',

        ),

        BottomNavigationBarItem(

          icon: Icon(Icons.settings),

          label: 'Settings',

        ),

      ],

      currentIndex: _selectedIndex,

      selectedItemColor: Colors.blue,

      onTap: _onItemTapped,

    ),

  );

}

}


 
