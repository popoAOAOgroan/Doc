#ES6 REACT实用功能

###使用props为components动态增加属性
`class AutoloadingPostsGrid extends React.Component {
  render() {
    var {
      className,
      ...others,  // contains all properties of this.props except for className
    } = this.props;
    return (
      <div className={className}>
        <PostsGrid {...others} />
        <button onClick={this.handleLoadMoreClick}>Load more</button>
      </div>
    );
  }
}`

`<div {...this.props} className="override">
  …
</div>`

`<div className="base" {...this.props}>
  …
</div>`

###动态属性名
`class Form extends React.Component {
  onChange(inputName, e) {
    this.setState({
      [`${inputName}Value`]: e.target.value,
    });
  }
}`

###初始化props
`class Video extends React.Component {
  static defaultProps = {
    autoPlay: false,
    maxLoops: 10,
  }
  static propTypes = {
    autoPlay: React.PropTypes.bool.isRequired,
    maxLoops: React.PropTypes.number.isRequired,
    posterFrameSrc: React.PropTypes.string.isRequired,
    videoSrc: React.PropTypes.string.isRequired,
  }
  state = {
    loopsRemaining: this.props.maxLoops,
  }
}`

###声明组件
`// The ES6+ way
class EmbedModal extends React.Component {
  constructor(props) {
    super(props);
    // Operations usually carried out in componentWillMount go here
  }
}`

###初始化STATE
`//ES6
class Video extends React.Component {
    constructor(props){
        super(props);
        this.state = {
            loopsRemaining: this.props.maxLoops,
        };
    }
}`

###定义默认属性和默认类型
`class Video extends React.Component {
    static defaultProps = {
        autoPlay: false,
        maxLoops: 10,
    };  // 注意这里有分号
    static propTypes = {
        autoPlay: React.PropTypes.bool.isRequired,
        maxLoops: React.PropTypes.number.isRequired,
        posterFrameSrc: React.PropTypes.string.isRequired,
        videoSrc: React.PropTypes.string.isRequired,
    };  // 注意这里有分号
    render() {
        return (
            <View />
        );
    } // 注意这里既没有分号也没有逗号
}`
