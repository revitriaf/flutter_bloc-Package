import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'package:flutter_bloc/flutter_bloc.dart';
import 'package:tugas12/color_bloc2.dart';
import 'package:tugas12/main_page.dart';
import 'package:tugas12/login_page.dart';


class Page2 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        home: BlocProvider<ColorBloc>(
          builder: (context) => ColorBloc(),
            child: MainPage1()),
    );
  }
}

class MainPage1 extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    ColorBloc bloc = BlocProvider.of<ColorBloc>(context);
    return Scaffold(
      floatingActionButton: Row(
        mainAxisAlignment: MainAxisAlignment.end,
        children: <Widget>[
          FloatingActionButton(heroTag: "btn4", backgroundColor: Colors.amber, onPressed: () {
            bloc.dispatch(ColorEvent.to_amber);
          },),
          SizedBox(width: 10,),
          FloatingActionButton(heroTag: "btn5", backgroundColor: Colors.lightBlue, onPressed: () {
            bloc.dispatch(ColorEvent.to_light_blue);
          },),
          SizedBox(width: 80,),
          FloatingActionButton(
            heroTag: "btn6",
            child: Text("Login"),
            onPressed: () {
              Navigator.pushReplacement(context, MaterialPageRoute(
                  builder: (context){
                    return LoginPage();
                  }));
            },
          ),
          SizedBox(width: 10,),
          FloatingActionButton(
            heroTag: "btn7",
            child: Text("Back"),
            onPressed: () {
              Navigator.pushReplacement(context, MaterialPageRoute(
                  builder: (context){
                    return MainPage();
                  }));
            },
          ),
        ],
      ),
      appBar: AppBar(title: Text("Flutter_bloc"),),
      body: Center(
        child: BlocBuilder<ColorBloc, Color>(
          builder: (context, currentColor) => AnimatedContainer(
          width: 100,
          height: 100,
          color: currentColor,
          duration: Duration(milliseconds: 500),
        ),
        ),
      ),
    );
  }
}
