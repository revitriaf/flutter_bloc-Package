import 'color_bloc.dart';
import 'package:tugas12/page_2.dart';
import 'package:flutter/material.dart';


class MainPage extends StatefulWidget {
  @override
  _MainPageState createState() => _MainPageState();
}

class _MainPageState extends State<MainPage> {
  ColorBloc bloc = ColorBloc();

  @override
  void dispose(){
    bloc.dispose;
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        floatingActionButton: Row(
          mainAxisAlignment: MainAxisAlignment.end,
          children: <Widget>[
            FloatingActionButton(
              heroTag: "btn1",
              backgroundColor: Colors.amber,
              onPressed: () {
                bloc.eventSink.add(ColorEvent.to_amber);
              },),
            SizedBox(width: 10,),
            FloatingActionButton(
              heroTag: "btn2",
              onPressed: () {
              bloc.eventSink.add(ColorEvent.to_light_blue);
            },
            backgroundColor: Colors.lightBlue,),
            SizedBox(width: 10,),
            FloatingActionButton(
              heroTag: "btn3",
              child: Text("Next"),
              onPressed: () {
                Navigator.pushReplacement(context, MaterialPageRoute(
                    builder: (context){
                      return Page2();
                    }));
              },
            ),
          ],
        ),
        appBar: AppBar(
          title: Text("Revi Tri A - 20170801297"),),
        body: Center(
          child: StreamBuilder(
            stream: bloc.stateSteam,
            initialData: Colors.amber,
            builder: (context, snapshot){
              return AnimatedContainer(
                duration: Duration(milliseconds: 500),
                width: 100,
                height: 100,
                color: snapshot.data,
              );
            },
          ),
        ),
      ),
    );
  }
}


