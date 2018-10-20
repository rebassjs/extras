
# Rebass Extras

Reference components for using styled-system to build custom styled components. Copy and paste these components and customize them however you see fit.

## Hide

```jsx
import React from 'react'
import styled from 'styled-components'
import { display } from 'styled-system'
import hoistStatics from 'hoist-non-react-statics'
import { Box } from 'rebass'

const mapProps = map => Component =>
  hoistStatics(props => <Component {...map(props)} />, Component)

export const Base = styled(Box)(display)

export const Hide = mapProps(({
  xsmall,
  small,
  medium,
  large,
  xlarge,
  display,
  ...props,
}) => ({
  display: display || [
    xsmall,
    small,
    medium,
    large,
    xlarge
  ].map(n => n ? 'none' : 'block'),
  ...props,
}))(Base)

export default Hide
```

```jsx
<Hide xsmall small />
```

## Position

```jsx
import styled from 'styled-components'
import {
  position,
  zIndex,
  top,
  right,
  bottom,
  left,
} from 'styled-system'
import { Box } from 'rebass'

export const Position = styled(Box)(
  position,
  zIndex,
  top,
  right,
  bottom,
  left
)

export const Relative = styled(Position)([])

Relative.defaultProps = {
  position: 'relative'
}

export const Absolute = styled(Position)([])

Absolute.defaultProps = {
  position: 'absolute'
}

export const Fixed = styled(Position)([])

Fixed.defaultProps = {
  position: 'fixed'
}

export const Sticky = styled(Position)([])

Sticky.defaultProps = {
  position: 'sticky'
}
```

