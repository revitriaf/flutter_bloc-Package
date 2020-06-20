import 'package:flutter/material.dart';
import 'package:tugas12/main_page.dart';


class LoginPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: RaisedButton(
            child: Text("Masuk"),
            onPressed: () {
              Navigator.pushReplacement(context, MaterialPageRoute(
                  builder: (context) {
                    return MainPage();
                  }));
            }
        ),
      ),
    );
  }
}
