#More React

```html
<script type="text/babel">
  var Circle = React.createClass({
    handleClick: function(){
      // alert('clicked ' + this.props.color + ' circle' );
      this.props.notifyParent();
    },
    render: function() {
      var styles = {backgroundColor: this.props.color, borderRadius: "30px",
                    width: "50px", height: "50px", float: "left"};
      return <div style={styles} onClick={this.handleClick}></div>;
    }
  });
  var Shape = React.createClass({
    getInitialState: function() {
      return { clickCount: 0 };
    },
    incrementCount: function(){
      this.setState({clickCount: this.state.clickCount + 1});
    },
    circles: function() {
      return this.props.circleColors.map(function(color, index){
        return <Circle color={color} key={index} notifyParent={this.incrementCount} />;
      }.bind(this));
    },
    render: function() {
      return <div style={this.props.style}>
              {this.circles()}
              <br />
              You clicked on: {this.state.clickCount} circle(s)
             </div>;
    }
  });
  var style1 = {height: "200px", width: "200px", backgroundColor: "red"};
  var style2 = {height: "300px", width: "300px", backgroundColor: "darkred"};

  ReactDOM.render(<Shape style={style1} circleColors={['blue', 'green', 'yellow']} />, document.getElementById('container-1'));

  ReactDOM.render(<Shape style={style2} circleColors={['grey', 'white','blue', 'green', 'yellow']} />, document.getElementById('container-2'));
</script>
```
